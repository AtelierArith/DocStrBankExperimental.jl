```
Kucoin.place_market_order(api_data[; <keyword arguments>]]) -> JSON3.Object
```

マーケットオーダーを出します。詳細についてはKucoinの公式[ドキュメント](https://docs.kucoin.com/#place-a-new-order)を参照してください。

# 引数

  * `api_data::UserApiData`: APIキー、シークレット、パスフレーズなどのユーザーAPIデータを保持します。

# キーワード

  * `size::String`: [オプション] 基本通貨での希望額。`size`または`funds`のいずれかのパラメータを使用する必要があります。
  * `funds::String`: [オプション] 使用する見積もり通貨の希望額。`size`または`funds`のいずれかのパラメータを使用する必要があります。
  * `client_order_id::String`: ユーザーが自分の注文を識別するために作成したユニークな注文ID、例: UUID
  * `side::String`: `"buy"`または`"sell"`
  * `symbol::String`: 有効な取引シンボルコード。例: `"ETH-BTC"`
  * `remark::String`: [オプション] 注文の備考、長さは100 utf-8文字を超えてはいけません。
  * `stp::String`: [オプション] 自己取引防止、有効な値: `"CN"`、`"CO"`、`"CB"`または`"DC"`、[自己取引防止](https://docs.kucoin.com/#self-trade-prevention)を参照してください。

# 戻り値

  * `JSON3.Object`

```json
{
  "orderId": "5bd6e9286d99522a52e458de"
}
```
