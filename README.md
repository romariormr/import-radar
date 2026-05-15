# Import Radar

> Extensão Chrome para compradores brasileiros no **Goofish (Xianyu/闲鱼)** da Alibaba.

Filtra produtos por perfil, verifica compatibilidade de rede com o Brasil, mostra preços em reais e gera links diretos para importação via CSSBuy.

---

## Instalar na Chrome Web Store

<a href="https://chromewebstore.google.com/detail/import-radar/pfgmdbacmfgchecnhbdhiememilpdngc">
  <img src="https://storage.googleapis.com/web-dev-uploads/image/WlD8wC6g8khYWPJUsQceQkhXSlv1/iNEddTyWiMfLSwFD6qGq.png" alt="Disponível na Chrome Web Store" width="220"/>
</a>

**Compatível com Chrome e Brave.**

> **Versão atual: v14.3** (2026-05-15) — veja [Novidades](#novidades) abaixo.

---

## O que faz

### Filtros por perfil de produto
Perfis pré-configurados para cada categoria:

| Perfil | O que filtra |
|--------|-------------|
| 📱 iPhone | Modelo, storage, cor, compatibilidade de rede BR (Band 28), carrier lock, dual SIM |
| 🤖 Android | Marca, modelo, compatibilidade BR |
| ⌚ Apple Watch | Série, tamanho, GPS/Cellular, eSIM BR |
| ⌚ Smartwatch | Marca, modelo (Garmin, Huawei, Samsung, Xiaomi…) |
| 🎾 Beach Tennis | Marca (Babolat, NOX, Head, CAMEWIN…), exclusão de falsos positivos |
| 💻 Notebook | Marca, modelo, storage, RAM |
| 🔍 Qualquer | Busca livre |

### Compatibilidade de rede
Para iPhones, verifica o modelo **A-number** contra a tabela oficial Apple — confirma suporte ao **Band 28 (700 MHz)** usado pelas operadoras brasileiras. Funciona para 500+ modelos.

### Detecção de bloqueio por operadora
Detecta automaticamente iPhones bloqueados por operadora — incluindo **卡贴机 / 有锁卡贴** (locked com adaptador RSIM, que funciona na China mas não no Brasil), `有锁`, carrier lock e SIM Bloqueado — e os marca com 🔒. Filtre para ocultar todos de uma vez. Itens identificados como `纯无锁` (totalmente desbloqueado) recebem o selo ✓ correspondente.

### Preço em reais em tempo real
Conversão CNY → BRL com taxa de mercado (Frankfurter) ou taxa customizada (ex: taxa CSSBuy). Filtro por preço mínimo e máximo em BRL ou CNY.

### Watchlist — Itens e Lojas Salvos
Salve produtos para comparar depois e monitore lojas favoritas — tudo dentro da extensão, sem precisar dos favoritos do navegador.

### Link direto para importação
Botão **"Importar agora"** em cada card leva direto ao CSSBuy com o produto mapeado — plataforma que recebe o produto na China e envia ao Brasil.

### Deep scrape de detalhes
Após varrer a listagem, a extensão busca a descrição completa de cada produto para detectar informações que só aparecem no anúncio individual (carrier lock, versão americana, etc.).

### Tradução automática PT-BR
Specs e descrição traduzidos automaticamente para português.

### Monitor de vendedores
Configure alertas por modelo, storage, cor e preço máximo. A extensão monitora automaticamente os vendedores salvos e notifica quando encontra correspondência.

### Chips dinâmicos por modelo
Após varrer uma página, a extensão gera automaticamente chips com os top 12 modelos encontrados (`iPhone 17 Pro Max (12)`, `iPad Air 5 (8)`, `Galaxy S24 (3)` …) — clique para filtrar e veja só o que importa.

### Faixa de preço
Quando um anúncio cobre múltiplas variantes (cor, storage) com preços diferentes — comum em lojas oficiais — o card exibe `¥X – ¥Y / R$min – R$max` em vez de só o preço mínimo.

### Banner inteligente de troca de perfil
Se o perfil ativo (ex: Smartphones) zera resultados mas a API trouxe itens de outra categoria (ex: 12 iPads), um banner sugere `📱 iPad` com botão direto para trocar.

### Alerta de múltiplos modelos
Anúncios que misturam 2+ modelos no mesmo item (`iPhone 17 e iPhone 17 Pro Max`, `13mini+14`, `苹果13和14`) recebem badge ⚠️ — você fica sabendo que o preço exibido pode não ser o do modelo que quer.

---

## Screenshots

![Screenshot 1](store-assets/store-screenshot-73.png)
![Screenshot 2](store-assets/store-screenshot-75.png)
![Screenshot 3](store-assets/store-screenshot-78.png)


> Usando a Chrome Web Store você recebe atualizações automáticas — recomendado.

---

## Privacidade

A extensão não coleta dados pessoais, não faz login e não envia informações para servidores externos.
Veja a [Política de Privacidade](https://romariormr.github.io/goofish-privacy/).

---

## Suporte

Encontrou um bug ou tem uma sugestão? Abra uma [issue](https://github.com/romariormr/import-radar/issues).

---

## Novidades

### v14.3 — 2026-05-15
- **Fix**: chips dinâmicos de modelo (`Apple Watch SE 2 (21)`, `iPhone 17 Pro (12)`, etc.) agora aparecem também no perfil **🔍 Qualquer**. Antes, só perfis específicos populavam os chips — o "Qualquer" deixava a área vazia.

### v14.2 — 2026-05-15
- **Fix**: perfil **🔍 Qualquer** não troca mais sozinho ao terminar o scan. Reportado pelo usuário: ao varrer uma página de vendedor com "Qualquer", o perfil era trocado automaticamente para Android. Removido o bloco legado que fazia essa auto-troca. O **banner de sugestão** da v14.1 continua ativo para o caso útil (quando um perfil específico zera resultados, oferece troca com botão).

### v14.1 — 2026-05-15
- **API-first scan**: a extensão agora intercepta as chamadas reais de API do Goofish em vez de parsear apenas o título dos cards. Resultado: dados muito mais completos (faixa de preço, tags de frete grátis, devolução grátis, envio em 48h).
- **`⏳ Verificando bloqueio…`** em vez de "Compatível" otimista para itens 美版 sem marcador explícito — evita o engano de marcar como compatível e depois descobrir que era `卡贴机`.
- **Detecção de `卡贴机` / `有锁卡贴`** como bloqueado (esses funcionam só na China com adaptador RSIM).
- **Faixa de preço** `¥X – ¥Y` exibida nos cards quando aplicável.
- **Badge ⚠️ Múltiplos modelos** para anúncios mistos.
- **Chips dinâmicos** com top 12 modelos por contagem real.
- **Banner de sugestão de perfil** quando o ativo zera resultados.
- **Parser expandido**: iPad (Air/Pro/mini), Apple/Honor/Xiaomi Watch, câmeras Fujifilm/Nikon/Sony/Canon, tablets Lenovo Legion/MatePad/Galaxy Tab, MacBook M-series, ThinkPad, ROG.
- **Robustez SPA**: MutationObserver aguarda o React renderizar antes do scan em `/personal`, `/search`, `/category`.

### v13.9 — 2026-05-12
- Removida a caixa de busca do painel — a busca do Goofish exige login com conta chinesa (passaporte) que estrangeiros não conseguem criar. Fluxo simplificado: usuário navega no Goofish e clica **Varrer**.

### v13.x — Maio 2026
- Dark mode v2 (cards, container de produto, carrossel).
- Detecção automática do scan após clicar **Buscar**.

> Para histórico técnico completo, consulte o repositório do código-fonte (privado).
