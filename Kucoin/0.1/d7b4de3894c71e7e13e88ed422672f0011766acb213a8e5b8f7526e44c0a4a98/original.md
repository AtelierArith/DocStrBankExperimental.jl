```
Kucoin.get_symbols_list([; market]) -> JSON3.Array{JSON3.Object}
```

Get a list of available currency pairs for trading. See Kucoin official  [docs](https://docs.kucoin.com/#get-symbols-list) for more details.

# Keywords

  * `market::String`: [Optional] a name of the trading market

# Returns

  * `JSON3.Array{JSON3.Object}`: a list of symbols for all or a specified markets

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
