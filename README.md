# 💎 GoldenScent Scraper API — GCC Perfumes & Arabian Oud Price Intelligence

<p align="center">
  <a href="https://console.apify.com/actors?search=goldenscent-scraper"><img src="https://img.shields.io/badge/Run%20on-Apify%20Store-orange?logo=apify&style=for-the-badge" alt="Run on Apify" /></a>
  <a href="#-python-quickstart"><img src="https://img.shields.io/badge/Python-3.8+-blue?logo=python&style=for-the-badge" alt="Python" /></a>
  <a href="#-nodejs-quickstart"><img src="https://img.shields.io/badge/Node.js-18+-green?logo=node.js&style=for-the-badge" alt="Node.js" /></a>
  <a href="#-pricing"><img src="https://img.shields.io/badge/Pricing-Pay--Per--Event%20($2.50%2F1k)-brightgreen?style=for-the-badge" alt="Pay Per Event" /></a>
</p>

> 🌐 **Tracking the broader GCC fragrance & beauty market?** Check out our sibling APIs:
> | Marketplace | Official Scraper Client | Market Focus |
> |---|---|---|
> | **GoldenScent** | **This API Client (`goldenscent-scraper`)** | Gulf designer & Arabian oud (`goldenscent.com`) |
> | **NiceOne Saudi Arabia** | [NiceOne Scraper API](https://github.com/your-username/niceone-scraper-api) | KSA beauty unicorn (`niceonesa.com`) |
> | **Boutiqaat** | [Boutiqaat Scraper API](https://github.com/your-username/boutiqaat-scraper-api) | Kuwait & celebrity beauty exclusives (`boutiqaat.com`) |

---

The unofficial Node.js & Python client, SDK wrapper, and automation templates for the **GoldenScent Scraper Apify Actor** (`goldenscent.com`).

Extract live designer perfumes, niche Arabian oud, oriental bakhoor, and luxury beauty prices across Saudi Arabia (`SAR`) and the UAE (`AED`), discount percentages, stock availability, and deep **Olfactory Pyramid fragrance notes (Top, Middle, Base)**.

---

## ⚡ Quickstart

### 🐍 Python Quickstart
```python
import os
from apify_client import ApifyClient

client = ApifyClient(os.getenv("APIFY_TOKEN", "YOUR_APIFY_TOKEN"))

run_input = {
    "platform": "goldenscent.com",
    "countryStorefront": "sa-SAR",
    "searchQueries": ["Chanel", "Tom Ford", "Oud", "Lattafa"],
    "maxItemsPerSource": 25,
    "onlyNewOrPriceChanged": True, # Delta monitor mode
}

run = client.actor("goldenscent-scraper").call(run_input=run_input)
items = client.dataset(run["defaultDatasetId"]).list_items().items

for p in items:
    print(f"[GoldenScent] {p['title']} - {p['salePrice']} {p['currency']}")
```

### 📦 Node.js Quickstart
```javascript
import { ApifyClient } from 'apify-client';

const client = new ApifyClient({ token: process.env.APIFY_TOKEN });

const run = await client.actor('goldenscent-scraper').call({
    platform: 'goldenscent.com',
    countryStorefront: 'sa-SAR',
    searchQueries: ['Chanel', 'Oud'],
    maxItemsPerSource: 25,
    onlyNewOrPriceChanged: true,
});

const { items } = await client.dataset(run.defaultDatasetId).listItems();
console.log(`Extracted ${items.length} products from GoldenScent`);
```

---

## 🔄 Salla (سلة) & n8n Price Alert Webhook Template

Looking to trigger automatic price-drop alerts or synchronize prices with your **Salla (سلة)** or **Zid (زد)** store?

Check out our production-ready n8n template:
- 📁 [`templates/n8n-salla-price-alert-workflow.json`](./templates/n8n-salla-price-alert-workflow.json): Import directly into n8n.
- 📁 [`templates/salla-price-alert-webhook.js`](./templates/salla-price-alert-webhook.js): Standalone Node.js Express webhook server.
- 📖 [`templates/README.md`](./templates/README.md): Setup instructions for Telegram alerts and Salla Merchant API.

---

## 🇸🇦 أداة سحب ومراقبة أسعار قولدن سنت (GoldenScent API)
واجهة برمجية متخصصة لمراقبة وتتبع أسعار العطور الأصلية والعود والبخور على موقع **قولدن سنت (GoldenScent)** في السعودية والإمارات:
- سحب الأسعار بالريال السعودي (SAR) والدرهم الإماراتي (AED).
- استخراج تفاصيل العطر، الحجم، التركيز (Eau de Parfum, EDT, Extrait de Parfum)، ونسبة الخصم.
- رصد عروض التخفيضات اليومية ومواسم العروض عبر Webhook و n8n.

---

## 📄 License
MIT © 2026
