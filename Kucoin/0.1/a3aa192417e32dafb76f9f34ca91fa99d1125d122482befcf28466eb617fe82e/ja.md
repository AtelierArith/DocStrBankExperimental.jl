```
Kucoin.cancel_all_orders(api_data[; symbol[, trade_type]]]) -> Union{JSON3.Array{String},JSON3.Array{Union{}}}
```

すべてのオープンオーダーをキャンセルします。詳細については、Kucoinの公式[ドキュメント](https://docs.kucoin.com/#cancel-all-orders)を参照してください。

# 引数

  * `api_data::UserApiData`: ユーザーAPIデータ（APIキー、シークレット、パスフレーズなど）を保持します。

# キーワード

  * `symbol::String`: [オプション] 取引ペアの有効なシンボルコード
  * `trade_type::String`: [オプション] 指定された取引タイプのオーダーをキャンセルするための取引の種類で、デフォルトはスポット取引オーダー（`TRADE`）をキャンセルします。

# 戻り値

  * `Union{JSON3.Array{String},JSON3.Array{Union{}}}`: キャンセルされたオーダーのIDのリスト

```json
[
  "5c52e11203aa677f33e493fb",  //orderId
  "5c52e12103aa677f33e493fe",
  "5c52e12a03aa677f33e49401",
  "5c626b0803aa676fee8412a2"
]
```
