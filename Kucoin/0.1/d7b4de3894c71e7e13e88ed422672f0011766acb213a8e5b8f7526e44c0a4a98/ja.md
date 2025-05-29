```
Kucoin.get_symbols_list([; market]) -> JSON3.Array{JSON3.Object}
```

取引のために利用可能な通貨ペアのリストを取得します。詳細については、Kucoinの公式 [docs](https://docs.kucoin.com/#get-symbols-list) を参照してください。

# キーワード

  * `market::String`: [オプション] 取引市場の名前

# 戻り値

  * `JSON3.Array{JSON3.Object}`: すべてまたは指定された市場のシンボルのリスト

```json
[
  ...
  {
    "symbol": "XLM-USDT",
    "name": "XLM-USDT",
    "baseCurrency": "XLM",
    "quoteCurrency": "USDT",
    "feeCurrency": "USDT",
    "market": "USDS",
    "baseMinSize": "0.1",
    "quoteMinSize": "0.01",
    "baseMaxSize": "10000000000",
    "quoteMaxSize": "99999999",
    "baseIncrement": "0.0001",
    "quoteIncrement": "0.000001",
    "priceIncrement": "0.000001",
    "priceLimitRate": "0.1",
    "isMarginEnabled": true,
    "enableTrading": true
  },
  ...
]
```
