# Aura — Plataforma de Gestão de Projetos

Plataforma web para freelancers e pequenas agências gerenciarem projetos, clientes e precificação de forma centralizada — com visão financeira clara sobre receita estimada vs. realizada.

🔗 **Demo:** work-aura.lovable.app

![Dashboard](./prints/dashboard.png)

## Sobre o projeto

A Aura nasceu de um problema real: freelancers e pequenas operações de serviço costumam controlar projetos, clientes e precificação em planilhas soltas, sem visão consolidada de quanto estão faturando, quais projetos estão atrasados e qual preço cobrar por hora considerando complexidade e custos extras.

O projeto foi construído com **Lovable**, uma ferramenta de desenvolvimento via IA generativa (geração de código a partir de prompts em linguagem natural). Sou transparente sobre isso: meu papel aqui foi de **product owner e arquiteto de regras de negócio** — defini a estrutura de dados, as métricas que importavam, as regras de cálculo e a experiência do usuário, e usei IA generativa para acelerar a implementação.

## Funcionalidades

- **Dashboard** — visão geral com projetos totais, projetos ativos, receita estimada e prazos próximos, além de gráfico de evolução de projetos ao longo do tempo.
- **Gestão de Projetos** — listagem com filtros por status, prazo e cliente, com alertas visuais de atraso (ex: "42d atrasado").
- **Clientes** — cadastro com contagem de projetos vinculados por cliente.
- **Financeiro** — comparativo entre receita estimada e realizada por mês, distribuição de receita por status (em andamento, concluído, pausado, cancelado) e tabela detalhada de projetos no período.
- **Calculadora de Precificação** — sugestão de valor de projeto a partir de valor/hora, horas estimadas, nível de complexidade (com multiplicador) e custos adicionais configuráveis.
- **Configurações** — parâmetros padrão de precificação (valor/hora, margem de lucro, complexidade padrão) para agilizar novos cálculos.

## Decisões de produto e lógica de negócio

Alguns pontos que exigiram pensar como dados de negócio se conectam:

- **Separação entre receita estimada e realizada**: projetos "em andamento" contam como estimativa, só viram receita realizada quando o status muda para "concluído". Isso evita o erro comum de tratar pipeline como faturamento.
- **Cálculo de precificação**: valor base (valor/hora × horas estimadas) multiplicado pelo fator de complexidade, somado a custos extras configuráveis — com parâmetros padrão salvos para reuso.
- **Alertas de prazo**: cálculo de dias de atraso a partir da data de entrega, sinalizado visualmente para priorização rápida.
- **Distribuição percentual por status**: cada status financeiro mostra seu percentual sobre o total do período, facilitando leitura de saúde do pipeline.

## Stack

- Frontend gerado via **Lovable** (React + Tailwind, sob o capô)
- Hospedagem própria do Lovable

## Por que esse projeto está aqui

Esse repositório não é uma demonstração de código escrito à mão — é uma demonstração de como eu penso estrutura de dados, métricas e regras de negócio na hora de desenhar um produto. Para projetos com foco técnico em SQL, ETL e modelagem de dados, veja https://work-aura.lovable.app/login
