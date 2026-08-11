# Solclor Piscinas — Landing Page Profissional

Landing page da **linha profissional Solclor para piscinas** — venda direto da fábrica para piscineiros, lojas, revendedores, distribuidores, condomínios e hotéis.

**Produção:** https://piscinas.solclor.com.br
**User cPanel VPS Dros HostGator:** `solclorpiscinas`

## Sections

1. **Hero** — split dark navy + banner piscina + CTA verde "Quero comprar direto da fábrica"
2. **Features (4 destaques)** — Qualidade premium · Compra direta da fábrica · Menor custo por piscina · Mais margem no serviço
3. **Why (7 pilares)** — Por que trabalhar com a linha profissional Solclor
4. **Compare** — Por que comprar da Solclor se já existem grandes marcas + selo com escudo
5. **Audiences (4 públicos)** — Piscineiros · Lojas · Distribuidores · Condomínios
6. **Line-full (8 categorias)** — Manutenção, Água e saúde, Água limpa, Prevenção e algas, Correção pH, Desinfecção, Limpeza, Acessórios
7. **Form** — Cadastro completo com segmento, necessidade, volume mensal
8. **Footer** — Logo + tagline + contatos + 4 features + copyright

## Stack

- HTML + CSS + JS (single-file, sem build)
- Imagens WebP com fallback JPG (`<picture>` + `image-set()`)
- Google Apps Script pra webhook do formulário (TODO: publicar e colar URL)
- Deploy: VPS HostGator Dros (cPanel + git pull)

## Otimizações aplicadas

- SEO completo: title, description, keywords, Open Graph, Twitter Cards, canonical, robots
- JSON-LD structured data: Organization, WebSite, Service, Product
- Imagens otimizadas (~11MB → ~740KB total)
- `content-visibility: auto` nas sections abaixo da dobra
- Preload crítico do banner hero + logo com `fetchpriority="high"`
- Intersection Observer pra reveal on scroll (fade + slide-up)
- `prefers-reduced-motion` respeitado
- Menu mobile animado (fade + slide-down + stagger dos itens)
- Design tokens: `--brand-dark` #0B2942, `--brand-cyan` #38BDF8, `--brand-green` #22C55E

## Deploy

```bash
# na VPS Dros HostGator (162.214.146.220)
sudo -u solclorpiscinas bash -c '
  cd /home/solclorpiscinas/public_html/ &&
  rm -rf cgi-bin index.html .htaccess 2>/dev/null;
  git init &&
  git symbolic-ref HEAD refs/heads/main &&
  git remote add origin https://github.com/soaresjoaoluiz1/solclor-piscinas.git &&
  git fetch origin main &&
  git reset --hard FETCH_HEAD
'
```
