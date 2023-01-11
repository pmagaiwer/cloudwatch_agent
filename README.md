# RESUMO:<br>
Configuração do CloudWatch para coleta métricas de mem/disco

Executar as seguintes linhas no terminal: (usar install_sp.sh se estiver em SP)

# Download<br>
wget https://s3.sa-east-1.amazonaws.com/amazoncloudwatch-agent-sa-east-1/amazon_linux/amd64/latest/amazon-cloudwatch-agent.rpm

# Install<br>
sudo rpm -U ./amazon-cloudwatch-agent.rpm

# Criar arquivo de configuração<br>
sudo /opt/aws/amazon-cloudwatch-agent/bin/amazon-cloudwatch-agent-config-wizard

# Arquivo de configuração<br>
/opt/aws/amazon-cloudwatch-agent/bin/config.json <br>

mkdir -p /usr/share/collectd/<br>
touch /usr/share/collectd/types.db<br>

# Subir o  agent<br>
sudo /opt/aws/amazon-cloudwatch-agent/bin/amazon-cloudwatch-agent-ctl -a fetch-config -m ec2 -c file:/opt/aws/amazon-cloudwatch-agent/bin/config.json  -s<br>

sudo systemctl enable amazon-cloudwatch-agent.service<br>
sudo systemctl start amazon-cloudwatch-agent.service<br>
sudo systemctl status amazon-cloudwatch-agent.service<br>
