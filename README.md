# aws-infra-atividade

<b>Link para o vídeo em que realizo Acesso à instância EC2 via SSH.</b>
[https://youtu.be/GKhZ1XsR-V4](https://www.youtube.com/watch?v=GKhZ1XsR-V4)

<b>Link para o vídeo em que realizo a demonstração da conexão bem-sucedida ao banco RDS.</b>
https://youtu.be/8W-ZyxcyFwU?si=nil5bxbWyNudP8ib

Este documento descreve os passos que realizei para configurar a infraestrutura na AWS, incluindo a criação de grupos de segurança, instância EC2 e banco de dados RDS PostgreSQL.

Passo a Passo:
<b>Criar Security Groups (Grupos de Segurança)</b>

1º. Criar um Security Group aws_ec2

Acessei o console da AWS e fui até a seção "Security Groups".
Cliquei em "Create Security Group".
Defini um nome e uma descrição para o grupo.

<b>Adicionei as regras de entrada:</b>

Permiti acesso SSH (porta 22) apenas para o meu IP pessoal.

Permiti acesso HTTP (porta 3000) ou Custom para qualquer IP (0.0.0.0/0).

<b>Salvei o Security Group.</b>

b. Criar um Security Group aws_rds

Ainda na seção "Security Groups", cliquei em "Create Security Group".

Defini um nome e uma descrição para o grupo.

<b>Adicionei a regra de entrada:</b>

Permiti conexão PostgreSQL (porta 5432) apenas para o Security Group da EC2 que criei anteriormente.

Salvei o Security Group.

<b>Criar uma Instância EC2 (aws_ec2)</b>

Acessei o console da AWS e fui até "EC2" > "Instances".

Cliquei em "Launch Instance".

Escolhi a AMI "Amazon Linux".

Escolhi o tipo de instância conforme necessário.

No passo de configuração de segurança, associei o Security Group aws_ec2 e aws_rds.

Escolhi ou criei um par de chaves (key_two_aws.pem) para acesso SSH e fiz o download.

Cliquei em "Launch" para criar a instância.

<b>Criar um Banco de Dados via RDS (aws-db)</b>

a. Criar um Banco de Dados PostgreSQL

Acessei o console da AWS e fui até "RDS".

Cliquei em "Create Database".

Escolhi o motor de banco de dados "PostgreSQL".

<b>Defini as configurações:</b>

Tipo de instância conforme necessário.

Usuário e senha para acesso ao banco de dados.

Security Group (aws_rds) criado para o RDS.

O nome do banco inicial não foi necessário pois minha aplicação utiliza Ruby on Rails, já tendo o comando de rails db:create, rails db:migrate.

<b>Finalizei a criação do banco de dados.</b>

Após a criação, anotei o endpoint do banco de dados gerado para conexão futura.

<b>No repositório tenho todas as imagens e vídeos pedidos na atividade.</b>
