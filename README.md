# df-ammo-prices

三角洲行动（Delta Force）弹药市场价格数据 + **在线估价 Agent** —— 自动从 [orzice.com](https://orzice.com) 抓取。

## 在线版

打开 → **https://summy00.github.io/df-ammo-prices/agent.html**

填 API Key + Base URL + 模型，粘截图，点计算。详见页面里的输入框。

## 数据

- **`ammo_prices.json`** — 完整目录（88 条左右，5 个等级）

字段说明：

| 字段 | 类型 | 说明 |
|---|---|---|
| `scraped_at` | ISO 时间戳 | 抓取时刻 (UTC) |
| `total` | int | 条目数 |
| `priced` | int | 有市价的条目数 |
| `items[].id` | int | orzice 内部 id |
| `items[].name` | str | 弹药名（如 `7.62x39mm AP`） |
| `items[].grade` | 1–5 | 品质（白/绿/蓝/紫/金） |
| `items[].method` | str | 获取方式（如 `交易行上架`） |
| `items[].icon_game` | url | 游戏官方图标 |
| `items[].icon_orzice` | url | orzice 缩略图 |
| `items[].current_price` | int | 当前市价（哈夫币） |

## 用法

直接 fetch：

```js
const r = await fetch("https://raw.githubusercontent.com/summy00/df-ammo-prices/main/ammo_prices.json");
const data = await r.json();
```

## 更新频率

按需手动 / 计划任务定期推送。`scraped_at` 字段是真值，超过 24h 视为过期。

## 来源声明

价格数据归 orzice.com 与游戏《三角洲行动》（腾讯）所有，本仓库仅作个人使用与分享。
