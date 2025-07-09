# Projeto de Pentest em Ambiente Controlado: Exploração de RDP no Windows Server 2022

## 1. Resumo Executivo
Este projeto demonstra o ciclo de vida de um pentest no serviço Remote Desktop Protocol (RDP) de um ambiente Windows Server 2022, cobrindo as fases de reconhecimento, enumeração, exploração de força bruta e acesso inicial. O objetivo principal foi identificar e explorar uma vulnerabilidade de credenciais fracas para obter acesso ao sistema.

## 2. Objetivo do Projeto
* Simular um cenário de ataque a um serviço RDP.
* Praticar o uso de ferramentas de varredura e quebra de senha.
* Demonstrar o processo de enumeração, exploração e acesso inicial a um sistema Windows Server.
* Familiarizar-se com a resolução de problemas em um ambiente de teste.

## 3. Ambiente do Laboratório

### Topologia da Rede
O laboratório consistiu em duas máquinas virtuais configuradas no VirtualBox (ou VMware), em uma rede interna/host-only:
* **Máquina Atacante:** Kali Linux (IP: `192.168.56.101`)
* **Máquina Alvo:** Windows Server 2022 Standard Evaluation (IP: `192.168.56.105`)

+----------------+      +------------------+
|   Kali Linux   |<---->| Windows Server 22|
| 192.168.56.101 |      | 192.168.56.105   |
+----------------+      +------------------+
        (Rede Interna/Host-Only)

### Configurações Importantes do Alvo (Windows Server 2022)
* **Remote Desktop:** Configurado como `Enabled (all clients)`.
* **Permissões de RDP:** O usuário `Administrator` foi adicionado ao grupo `Remote Desktop Users` para permitir o acesso.

## 4. Metodologia e Ferramentas Utilizadas
* **Reconhecimento e Enumeração:** Nmap (varredura de portas, detecção de serviço, NSE scripts).
* **Exploração:** Hydra (força bruta de senhas RDP).
* **Acesso e Pós-Exploração:** `xfreerdp3` (cliente RDP), comandos nativos do Windows (`ipconfig`, `net user`, `net localgroup`, `tasklist`).

## 5. Execução do Pentest (Passo a Passo com Evidências)

### 5.1. Configuração Inicial e Verificação de Conectividade
- IPs das VMs: Kali (`192.168.56.101`), Windows Server (`192.168.56.105`).
- Teste de conectividade com `ping` bem-sucedido.

```bash
ping 192.168.56.105

