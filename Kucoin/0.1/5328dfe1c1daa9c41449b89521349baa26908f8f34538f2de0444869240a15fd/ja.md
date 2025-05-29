```
Kucoin.get_all_tickers() -> JSON3.Array{JSON3.Object}
```

市場のすべての取引ペアの市場情報を取得します。詳細については、Kucoinの公式 [docs](https://docs.kucoin.com/#get-all-tickers) を参照してください。

# 戻り値

  * `JSON3.Array{JSON3.Object}`

```json
[
  {
    "symbol": "BTC-USDT",  // シンボル
    "symbolName":"BTC-USDT",  // 取引ペアの名前、名前変更後に変更される
    "buy": "11328.9",  // 最良売り価格
    "sell": "11329",  // 最良買い価格
    "changeRate": "-0.0055",  // 24時間の変化率
    "changePrice": "-63.6",  // 24時間の変化価格
    "high": "11610",  // 24時間の最高価格
    "low": "11200",  // 24時間の最低価格
    "vol": "2282.70993217", // 24時間の取引量、BTCでの集計取引量
    "volValue": "25984946.157790431",  // 24時間の合計、過去24時間の見積もり通貨での取引量
    "last": "11328.9",  // 最終価格
    "averagePrice": "11360.66065903",  // 昨日の24時間の平均取引価格
    "takerFeeRate": "0.001",  // 基本テイカー手数料
    "makerFeeRate": "0.001",  // 基本メイカー手数料
    "takerCoefficient": "1",  // テイカー手数料係数
    "makerCoefficient": "1"  // メイカー手数料係数
  }
]
```
