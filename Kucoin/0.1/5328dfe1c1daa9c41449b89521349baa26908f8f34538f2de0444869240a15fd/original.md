```
Kucoin.get_all_tickers() -> JSON3.Array{JSON3.Object}
```

Get the market information for all the trading pairs in the market. See Kucoin official  [docs](https://docs.kucoin.com/#get-all-tickers) for more details.

# Returns

  * `JSON3.Array{JSON3.Object}`

```json
[
  {
    "symbol": "BTC-USDT",  // symbol
    "symbolName":"BTC-USDT",  // Name of trading pairs, it would change after renaming
    "buy": "11328.9",  // bestAsk
    "sell": "11329",  // bestBid
    "changeRate": "-0.0055",  // 24h change rate
    "changePrice": "-63.6",  // 24h change price
    "high": "11610",  // 24h highest price
    "low": "11200",  // 24h lowest price
    "vol": "2282.70993217", // 24h volume，the aggregated trading volume in BTC
    "volValue": "25984946.157790431",  // 24h total, the trading volume in quote currency of last 24 hours
    "last": "11328.9",  // last price
    "averagePrice": "11360.66065903",  // 24h average transaction price yesterday
    "takerFeeRate": "0.001",  // Basic Taker Fee
    "makerFeeRate": "0.001",  // Basic Maker Fee
    "takerCoefficient": "1",  // Taker Fee Coefficient
    "makerCoefficient": "1"  // Maker Fee Coefficient
  }
]
```
