#!/bin/bash

# Script para atualizar o Debian completamente

# Verifica se o script está sendo executado como root
if [ "$(id -u)" -ne 0 ]; then
    echo "Este script deve ser executado como root!"
    exit 1
fi

echo "Atualizando lista de pacotes..."
apt-get update -y

echo "Realizando atulização de pacotes..."
apt-get full-upgrade -y

echo "Removendo pacotes desnecessários..."
apt-get autoremove -y

echo "Limpando pacotes e cache..."
apt-get clean

echo "Atualizando os repositórios para a última versão estável..."
apt-get dist-upgrade -y

echo "Reiniciando o Sistema..."
reboot
