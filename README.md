# Implementação e Análise de um Bloqueador de Anúncios e Servidor DNS Recursivo em uma Rede Doméstica Utilizando Raspberry Pi

### Repositório do projeto e implementação de um servidor utilizando o Raspberry Pi 3 B+ com o Pi-hole (https://pi-hole.net/) e o Unbound (https://www.nlnetlabs.nl/projects/unbound/about/), com a finalidade de realizar o bloqueio de anúncios e a resolução de nomes localmente e abrangendo todos os dispositivos de uma rede local, tanto sem fio quando via ethernet.

Para a realização do projeto, foi necessário:

1. Instalar uma distribuição Linux compatível com Raspberry Pi:
  - A distribuição escolhida foi a Raspberry Pi OS (https://www.raspberrypi.com/software/)
2. Instalar o Pi-hole no Raspberry;
3. Instalar o Unbound no Raspberry;
4. Configurar o roteador doméstico local para utilizar o Raspberry como único servidor DNS disponível:
  - No caso, o roteador utilizado foi o AN5506-04-FA;
5. Utilizar o servidor por 20 dias, 24h por dia.

Para o uso e manutenção do projeto, alguns pacotes utilitários foram instalados, como:

- XRDP;
- TightVNCServer.

Para a instalação do Pi-hole, optou-se por utilizar o comando simplificado

```console
curl -sSL https://install.pi-hole.net | bash
```
e as configurações utilizadas foram as seguintes:

- Provedor DNS: Google (8.8.8.8);
- Lista de bloqueio padrão: Steven Black’s Unified Hosts List;
- Bloqueio de anúncios via IPv4;
- Definição de IP estático para o Raspberry como sendo 192.168.1.244;
- Instalação da interface web de administrador;
- Instalação do servidor web lighttpd;
- Salvamento automático de todos os logs.

Em seguida, o Unbound foi instalado:

```console
sudo apt install unbound
```
e o Pi-hole configurado para redirecionar a resolução de nomes para o localhost#5335 (Unbound).

Neste repositório encontra-se o arquivo pihole-FTL.db, contendo todos os logs e dados adquiridos durante a utilização do servidor, dispostos em 11 tabelas:

- addinfo_by_id
- aliasclient
- client_by_id
- counters
- domain_by_id
- forward_by_id
- ftl
- message
- network
- network_addresses
- query_storage.