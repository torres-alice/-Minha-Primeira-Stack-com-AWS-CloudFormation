#  Desafio: Implementando Minha Primeira Stack com AWS CloudFormation

> **Entrega do Desafio da DIO – Laboratório Prático com AWS CloudFormation**  
> Aluno: Alice Torres  
> Data: 28 de outubro de 2025  

##  Objetivo

Este repositório documenta a implementação da minha primeira **stack na AWS** utilizando **AWS CloudFormation**, conforme orientado nas aulas do laboratório da **Digital Innovation One (DIO)**. O objetivo é consolidar os conhecimentos adquiridos sobre **Infraestrutura como Código (IaC)**, boas práticas de documentação técnica e uso do GitHub como portfólio de aprendizado.

##  Conceitos Aplicados

Durante este desafio, foram aplicados os seguintes conceitos:

- **Infraestrutura como Código (IaC)**: Automatização da criação e gerenciamento de recursos na nuvem usando arquivos declarativos.
- **AWS CloudFormation**: Serviço da AWS que permite modelar e provisionar recursos de forma segura e previsível.
- **Templates YAML/JSON**: Estrutura usada para definir os recursos da stack (neste caso, utilizei YAML por sua legibilidade).
- **Stacks**: Conjunto de recursos AWS provisionados a partir de um único template.
- **Parâmetros, Mapeamentos, Condições e Saídas**: Elementos avançados de templates que permitem reutilização e flexibilidade.
- **Boas práticas de versionamento e documentação** com Git e GitHub.

##  Arquitetura Implementada

A stack criada neste laboratório provisiona os seguintes recursos na AWS:

- **1 Bucket S3** (com nome único e políticas de segurança básicas)
- **1 Instância EC2** (com AMI padrão, tipo t2.micro e security group permitindo tráfego HTTP/SSH)
- **1 Security Group** associado à instância EC2

>  **Importante**: Todos os recursos foram configurados para serem **excluídos automaticamente** ao deletar a stack, evitando custos residuais.


##  Template CloudFormation (Resumo)

O arquivo [`https://github.com/torres-alice/-Minha-Primeira-Stack-com-AWS-CloudFormation/blob/main/AWSTemplateFormatVersion.yaml`](cloudformation-template.yaml) contém:

- **Parâmetros**: Região, tipo de instância, nome do bucket.
- **Recursos**:
  - `MyS3Bucket`: Bucket S3 com nome gerado dinamicamente.
  - `WebServerSecurityGroup`: Permite tráfego nas portas 22 (SSH) e 80 (HTTP).
  - `WebServerInstance`: Instância EC2 com user data simples (ex: página HTML de exemplo).
- **Outputs**: URL do bucket S3 e IP público da instância EC2.

>  O template foi validado com o comando:
> ```bash
> aws cloudformation validate-template --template-body file://cloudformation-template.yaml
> ```



##  Lições Aprendidas

- **CloudFormation simplifica muito a replicação de ambientes** — basta um template para recriar toda a infra.
- **Erros comuns**: nomes de bucket S3 devem ser globalmente únicos; esquecer de liberar portas no security group quebra conectividade.
- **Documentar cada passo ajuda a fixar o conhecimento** e serve como referência futura.
- **Testar em sandbox antes de produção** é essencial — felizmente, a AWS oferece créditos gratuitos para laboratórios.

##  Recursos Utilizados

- [Documentação oficial do AWS CloudFormation](https://docs.aws.amazon.com/cloudformation/)
- Material complementar fornecido pela DIO: *Implementando sua Primeira Stack com AWS CloudFormation.zip*
- AWS Free Tier (para testes sem custo)

##  Conclusão

Este desafio foi fundamental para entender como a **Infraestrutura como Código** transforma a forma como desenvolvedores e DevOps interagem com a nuvem. Ao automatizar a criação de recursos, ganhamos em **consistência, segurança e escalabilidade**.

Estou empolgado para aplicar esses conceitos em projetos mais complexos, como pipelines CI/CD, ambientes multi-região e integração com outros serviços AWS (Lambda, RDS, etc.).



>  **"Automatize o chato, documente o importante."**  

