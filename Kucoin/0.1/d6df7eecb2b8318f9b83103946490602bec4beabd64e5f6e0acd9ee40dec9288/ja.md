```
Kucoin.get_trade_fees(api_data; symbols) -> JSON3.Array{JSON3.Object}
```

取引ペアの実際の手数料率を取得します。詳細については、Kucoinの公式 [docs](https://docs.kucoin.com/#actual-fee-rate-of-the-trading-pair) を参照してください。

# 引数

  * `api_data::UserApiData`: APIキー、シークレット、パスフレーズなどのユーザーAPIデータを保持します。
  * `symbols::AbstractVector{String}`: 取引ペア（オプション、最大10の取引ペアの手数料率を一度に照会できます）

# 戻り値

  * `JSON3.Array{JSON3.Object}`

```json
[
  {
    "symbol": "BTC-USDT",
    "takerFeeRate": "0.001",
    "makerFeeRate": "0.001"
  },
  {
    "symbol": "KCS-USDT",
    "takerFeeRate": "0.002",
    "makerFeeRate": "0.0005"
}
```
