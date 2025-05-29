```
Kucoin.place_limit_order(api_data[; <keyword arguments>]) -> JSON3.Object
```

リミットオーダーを出します。詳細についてはKucoinの公式[ドキュメント](https://docs.kucoin.com/#place-a-new-order)を参照してください。

# 引数

  * `api_data::UserApiData`: ユーザーのAPIデータ（APIキー、シークレット、パスフレーズなど）を保持します。

# キーワード

  * `price::String`: 見積もり通貨における基軸通貨の価格
  * `size::String`: 購入または販売する基軸通貨の量
  * `time_in_force::String`: [オプション] `"GTC"`、`"GTT"`、`"IOC"`、または`"FOK"`（デフォルトは`"GTC"`）、[Time In Force](https://docs.kucoin.com/#time-in-force)を参照してください。
  * `cancel_after::Int64`: [オプション] `n`秒後にキャンセル、`time_in_force`が`"GTT"`である必要があります。
  * `post_only::Bool`: [オプション] ポストオンリーフラグ、`time_in_force`が`"IOC"`または`"FOK"`のときは無効、[Post Only](https://docs.kucoin.com/#post-only)を参照してください。
  * `hidden::Bool`: [オプション] 注文は注文書に表示されません。
  * `iceberg::Bool`: [オプション] 注文の一部のみが注文書に表示されます。
  * `visible_size::String`: [オプション] アイスバーグ注文の最大表示サイズ。
  * `client_order_id::String`: ユーザーが自分の注文を識別するために作成したユニークな注文ID、例：UUID。
  * `side::String`: `"buy"`または`"sell"`。
  * `symbol::String`: 有効な取引シンボルコード。例：`"ETH-BTC"`。
  * `remark::String`: [オプション] 注文の備考、長さは100 UTF-8文字を超えてはいけません。
  * `stp::String`: [オプション] 自己取引防止、有効な値：`"CN"`、`"CO"`、`"CB"`または`"DC"`、[Self-Trade Prevention](https://docs.kucoin.com/#self-trade-prevention)を参照してください。
  * `trade_type::String`: [オプション] 取引の種類 `TRADE`（現物取引）、`MARGIN_TRADE`（マージン取引）。デフォルトは`TRADE`です。

# 戻り値

  * `JSON3.Object`

```json
{
  "orderId": "5bd6e9286d99522a52e458de"
}
```
