# Drogarias Ultra Popular - Pedidos WhatsApp

Um site de pedidos dinâmico e responsivo para a Drogarias Ultra Popular, permitindo que clientes selecionem produtos, variantes e quantidades, e enviem pedidos diretamente via WhatsApp.

## 🚀 Características

- **Carregamento Dinâmico de Produtos**: Todos os produtos são carregados a partir de um arquivo JSON (`public/data/products.json`)
- **Carrosséis de Variantes**: Produtos com múltiplas variantes (tamanhos, sabores, embalagens) com seletor interativo
- **Carrinho de Compras**: Sistema completo de carrinho com cálculo automático de subtotais e total
- **Integração WhatsApp**: Envia pedidos formatados diretamente para o WhatsApp da loja via `wa.me`
- **Mobile-First**: Design responsivo otimizado para dispositivos móveis
- **Sem Dependências Externas**: HTML, CSS e JavaScript puro - nenhuma dependência de build

## 📁 Estrutura de Arquivos

```
pedidos-whatsapp/
├── index.html                 # Arquivo principal (HTML + CSS + JavaScript)
├── public/
│   ├── data/
│   │   └── products.json      # Dados dos produtos (editável)
│   └── images/
│       ├── fralda-babysec.jpg
│       ├── mucilon.jpg
│       ├── toalha-bebe.jpg
│       ├── leite-ninho.jpg
│       ├── composto-lacteo.jpg
│       ├── formula-aptamil.jpg
│       ├── repelente-off.jpg
│       ├── nistatina-oxido.jpg
│       └── sabonete-granado.jpg
├── .github/
│   └── workflows/
│       └── pages.yml          # Workflow para GitHub Pages
└── README.md                  # Este arquivo
```

## 🛠️ Como Editar Produtos e Variantes

### 1. Adicionar/Editar Produtos

Edite o arquivo `public/data/products.json`:

```json
{
  "id": "identificador-unico",
  "name": "Nome do Produto",
  "price": 59.99,
  "image": "/images/nome-da-imagem.jpg",
  "category": "Fraldas",
  "variants": [
    { "id": "p", "label": "P", "value": "P" },
    { "id": "m", "label": "M", "value": "M" }
  ]
}
```

**Campos obrigatórios:**
- `id`: Identificador único (sem espaços, use hífens)
- `name`: Nome do produto
- `price`: Preço em formato numérico (ex: 59.99)
- `image`: Caminho da imagem (relativo a `public/`)
- `category`: Categoria para agrupamento (ex: "Fraldas", "Alimentos", "Higiene")
- `variants`: Array de variantes (pode ser vazio `[]` se não houver variantes)

### 2. Adicionar Imagens

1. Coloque a imagem na pasta `public/images/`
2. Use o caminho `/images/nome-da-imagem.jpg` no JSON

**Formatos suportados:** JPG, PNG, WebP

### 3. Editar Lojas e Números WhatsApp

No arquivo `index.html`, procure pela seção `<select id="store">` e edite as opções:

```html
<option value="5521987654321|Loja Centro">Loja Centro - (21) 98765-4321</option>
```

Formato: `NUMERO_WHATSAPP|NOME_DA_LOJA`

## 📱 Fluxo de Uso

1. **Selecionar Variante** (se aplicável): Escolha tamanho, sabor ou embalagem
2. **Ajustar Quantidade**: Use os botões + e - para definir a quantidade
3. **Adicionar ao Carrinho**: Clique em "Adicionar"
4. **Revisar Carrinho**: Veja o resumo de produtos e total
5. **Preencher Dados**: Nome, telefone, endereço, forma de pagamento
6. **Enviar Pedido**: Clique em "Enviar Pedido pelo WhatsApp"
7. **WhatsApp Abre**: A mensagem do pedido é enviada automaticamente para a loja

## 🚀 Publicação e Deploy

### GitHub Pages (Automático)

O repositório está configurado para publicar automaticamente no GitHub Pages:

1. Qualquer push para a branch `master` dispara o workflow de deploy
2. O site fica disponível em: `https://ultrapopularrio.github.io/pedidos-whatsapp/`
3. Alterações levam cerca de 1-2 minutos para aparecer online

### Atualizar Produtos Online

1. Edite o arquivo `public/data/products.json` no GitHub (ou localmente e faça push)
2. Aguarde 1-2 minutos para o site atualizar
3. Atualize o navegador para ver as mudanças

## 💻 Desenvolvimento Local

Para testar localmente antes de fazer push:

1. **Clonar o repositório:**
   ```bash
   git clone https://github.com/ultrapopularrio/pedidos-whatsapp.git
   cd pedidos-whatsapp
   ```

2. **Servir localmente:**
   ```bash
   # Usando Python 3
   python3 -m http.server 8000
   
   # Ou usando Node.js
   npx http-server
   ```

3. **Abrir no navegador:**
   ```
   http://localhost:8000
   ```

## 📝 Exemplo de Produto Completo

```json
{
  "id": "fralda-babysec-hiper",
  "name": "Fralda Baby Sec Hiper",
  "price": 59.99,
  "image": "/images/fralda-babysec.jpg",
  "category": "Fraldas",
  "variants": [
    { "id": "p", "label": "P", "value": "P" },
    { "id": "m", "label": "M", "value": "M" },
    { "id": "g", "label": "G", "value": "G" },
    { "id": "xg", "label": "XG", "value": "XG" }
  ]
}
```

## 🎨 Personalização

### Alterar Cores

Edite o arquivo `index.html` e procure pela seção `<style>`:

- **Cor Principal (Vermelho)**: Procure por `#E63946` e substitua pela cor desejada
- **Cor de Fundo**: Procure por `#f5f5f5` e substitua

### Alterar Logo

No `<header>`, edite a tag `<img src="...">`:

```html
<img src="https://seu-url-da-logo.com/logo.jpg" alt="Ultra Popular">
```

### Alterar Título

Edite a tag `<title>` e o `<h1>` no header.

## 🔧 Troubleshooting

### Imagens não aparecem
- Verifique se o caminho em `public/data/products.json` está correto
- Certifique-se de que a imagem está na pasta `public/images/`
- Atualize o navegador (Ctrl+Shift+R ou Cmd+Shift+R)

### Produtos não carregam
- Abra o console do navegador (F12) e procure por erros
- Verifique se o arquivo `public/data/products.json` está bem formatado (JSON válido)
- Certifique-se de que o arquivo não tem vírgulas extras ou faltantes

### WhatsApp não abre
- Verifique se o número de WhatsApp está no formato correto (apenas dígitos, com código do país)
- Teste o link manualmente: `https://wa.me/5521987654321?text=teste`

## 📞 Contato e Suporte

Para dúvidas ou sugestões, abra uma issue no repositório GitHub:
https://github.com/ultrapopularrio/pedidos-whatsapp/issues

## 📄 Licença

Este projeto é de código aberto e pode ser usado livremente pela Drogarias Ultra Popular.

---

**Versão:** 1.0.0  
**Última atualização:** Janeiro de 2026
