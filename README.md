# Matemago 1 — build WebGL

Build web do jogo **Matemago 1** (versão 0.2b), exportado pelo Unity para WebGL e executado direto no navegador, sem plugin. Este repositório guarda o jogo já compilado e pronto para ser servido como site estático.

> Este repositório contém **apenas o build exportado**. O projeto-fonte do Unity (cenas, scripts e assets originais) não está aqui.

<!-- Preencha com o seu contexto: seu papel no projeto e como o jogo foi migrado do Flash (ferramentas, decisões, desafios). Isso transforma este repositório em um case. -->

## Detalhes técnicos

Dados lidos do `Build/Build.json`:

| Item | Valor |
| --- | --- |
| Motor | Unity 2019.4.2f1 |
| Produto / versão | Matemago 1 / 0.2b |
| Saída | WebGL 2.0, com fallback para WebGL 1.0 |
| Código | WebAssembly, sem multithread |
| Tipo de build | Development build |
| Resolução do player | 960 × 600 (definida em `index.html`) |

## Estrutura

```
├── index.html        # Página que carrega o player Unity
├── Build/            # Build exportado (código WebAssembly, dados e loader)
│   ├── UnityLoader.js
│   ├── Build.json
│   └── Build.*.unityweb
└── TemplateData/     # Barra de progresso, favicon e estilos do template Unity
```

## Como executar localmente

O jogo precisa ser servido por HTTP; abrir o `index.html` direto do disco (`file://`) normalmente não funciona com o loader do Unity. Na raiz do repositório:

```bash
python3 -m http.server 8000
```

Depois acesse http://localhost:8000.

## Publicação

Como é um site estático, qualquer hospedagem estática serve (por exemplo, GitHub Pages). Algumas observações:

- O build é um **development build**, portanto maior e menos otimizado que um release build. Os arquivos principais somam cerca de 34 MB. Para uso em produção, gere um release build a partir do projeto-fonte.
- O loader é o formato antigo do Unity (`UnityLoader.js`, Unity 2019). A compatibilidade com navegadores atuais não foi testada.
