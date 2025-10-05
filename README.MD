# Hackathon Reusable Actions

Este repositório contém um conjunto de ações reutilizáveis do GitHub Actions para automação de fluxos de CI/CD, com foco em projetos que participam de hackathons ou que desejam padronizar pipelines de integração e entrega contínua.

## Sumário

- [Visão Geral](#visão-geral)
- [Estrutura do Repositório](#estrutura-do-repositório)
- [Como Usar](#como-usar)
- [Exemplos de Uso](#exemplos-de-uso)
- [Contribuindo](#contribuindo)
- [Licença](#licença)

---

## Visão Geral

O objetivo deste projeto é centralizar e compartilhar workflows do GitHub Actions que podem ser reutilizados em múltiplos repositórios, promovendo padronização, agilidade e melhores práticas em automação de pipelines.

## Estrutura do Repositório

```
hackathon-reusable-actions/
├── .gitignore
├── LICENSE
├── README.MD
└── .github/
    └── workflows/
        ├── reusable-ci.yml
        └── reusable-docker-build-push.yml
```

- **.github/workflows/reusable-ci.yml**: Workflow reutilizável para integração contínua (CI).
- **.github/workflows/reusable-docker-build-push.yml**: Workflow reutilizável para build e push de imagens Docker.

## Como Usar

Você pode reutilizar os workflows deste repositório em outros projetos utilizando a sintaxe `uses` do GitHub Actions. Basta referenciar o caminho do workflow desejado e a branch ou tag correspondente.

Exemplo de chamada em outro repositório:

```yaml
jobs:
  ci:
    uses: samuel/saint-espirit/.github/workflows/reusable-ci.yml@main
    with:
      # parâmetros de entrada, se houver
```

> Substitua `samuel/saint-espirit` pelo caminho correto do seu repositório e ajuste a branch/tag conforme necessário.

Considere o repositorio de contexto e crie uma documentação para o projeto em formato md no arquivo readme. Essa será a documentação para o retoritório no github
## Exemplos de Uso

### Integração Contínua (CI)

```yaml
name: CI

on:
  push:
    branches: [main]

jobs:
  ci:
    uses: samuel/saint-espirit/.github/workflows/reusable-ci.yml@main
```

### Build e Push de Docker

```yaml
name: Docker Build and Push

on:
  push:
    branches: [main]

jobs:
  docker:
    uses: samuel/saint-espirit/.github/workflows/reusable-docker-build-push.yml@main
    secrets:
      DOCKERHUB_USERNAME: ${{ secrets.DOCKERHUB_USERNAME }}
      DOCKERHUB_TOKEN: ${{ secrets.DOCKERHUB_TOKEN }}
```

## Contribuindo

Contribuições são bem-vindas! Sinta-se à vontade para abrir issues ou pull requests com melhorias, correções ou novos workflows reutilizáveis.

## Licença

Este projeto está licenciado sob os termos da licença MIT. Veja o arquivo [LICENSE](LICENSE) para mais detalhes.