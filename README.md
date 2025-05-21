# Criando e Configurando uma Máquina Virtual no Microsoft Azure

## 1. Acesso ao Azure Portal

1. [Azure Portal](https://portal.azure.com/).
2. Faça login com sua conta Microsoft.

## 2. Criando uma Máquina Virtual

### Etapa 1: Ir para "Máquinas Virtuais"

- No menu lateral esquerdo, clique em **“Máquinas virtuais”** > **“Criar”** > **“Máquina virtual”**.

### Etapa 2: Configurações básicas

Preencha os campos obrigatórios:

- **Assinatura e grupo de recursos**: Escolha ou crie um novo.
- **Nome da VM**: Ex: `vm-prod-app01`
- **Região**: Escolha uma máquina fora do Brasil para melhores custos
- **Imagem**: Escolha o SO (ex: Ubuntu, Windows Server, etc.).
- **Tamanho**: Escolha um SKU de acordo com a carga esperada (ex: `Standard_DS2_v2`).

### Etapa 3: Autenticação

- **Tipo de autenticação**: Par de chaves SSH (Linux) ou senha (Windows).
- Configure os dados de login.

## 3. Alta Disponibilidade e Escalabilidade

### a) Zona de disponibilidade

- Em “Opções de disponibilidade”, selecione:
  - **Zona de disponibilidade**: Distribui VMs entre data centers físicos, garantindo tolerância a falhas.

### b) Conjunto de disponibilidade (Availability Set)

- Alternativa às Zonas, útil para cargas em cluster. Garante redundância de hardware e balanceamento de atualização.

### c) Escalonamento automático (Auto-scale)

Após criar a VM:

1. Vá em **“Conjuntos de dimensionamento de máquinas virtuais”** para criar um conjunto de VMs idênticas com **escalabilidade automática**.
2. Configure regras de escalonamento com base em CPU, memória, etc.

## 4. Confiabilidade e Previsibilidade

### a) Tipo de disco

- Escolha discos gerenciados com **Premium SSD** para garantir alto desempenho com baixa latência e maior confiabilidade.

### b) Reserva de capacidade

- Use **VMs reservadas** (1 ou 3 anos) para workloads previsíveis e reduzir custos.

## 5. Segurança e Governança

### a) Grupo de Segurança de Rede (NSG)

- Configure regras de entrada/saída para restringir tráfego.
- Ex: Permitir somente portas 22 (SSH) ou 3389 (RDP).

### b) Azure Defender (Microsoft Defender for Cloud)

- Ative para análise contínua de vulnerabilidades, proteção contra ameaças e recomendações de segurança.

### c) Políticas de governança com Azure Policy

- Aplique políticas para exigir configurações seguras (ex: criptografia obrigatória, tipo de VM permitido).
- Ex: Bloquear criação de VMs dentro da região "Brazil South", evitando maiores custos.

## 6. Capacidade de Gerenciamento

### a) Tags (Etiquetas)

- Use tags para organizar e identificar recursos por ambiente, projeto, dono etc.
- Ex: `Ambiente=Produção`, `Aplicação=ERP`.

### b) Backup automático

- Habilite **Azure Backup** para proteção contínua dos dados.

### c) Atualizações automáticas

- Configure **Update Management** (com Azure Automation) para aplicar patches de segurança sem downtime.

### d) Extensões de VM

- Instale agentes (como o **Azure Diagnostics Agent** ou **Custom Script Extension**) para automatizar tarefas de configuração e coleta de dados.

## 7. Finalizar a Criação

1. Revise as configurações na aba **“Revisar + criar”**.
2. Clique em **“Criar”**.
3. Aguarde a implantação.

## Resumo: Pilares Atendidos

| **Pilar**                    | **Recursos Utilizados no Azure**                                  |
|-----------------------------|---------------------------------------------------------------------|
| **Alta disponibilidade**     | Zonas de disponibilidade, Conjuntos de disponibilidade            |
| **Escalabilidade**           | Conjuntos de dimensionamento com Auto-scale                       |
| **Confiabilidade**           | Premium SSD, Azure Monitor, Reserva de capacidade                 |
| **Segurança e Governança**   | NSG, Defender, Azure Policy, Managed Identity                     |
| **Gerenciamento**            | Tags, Backup, Update Management, Extensões, Azure Automation      |

