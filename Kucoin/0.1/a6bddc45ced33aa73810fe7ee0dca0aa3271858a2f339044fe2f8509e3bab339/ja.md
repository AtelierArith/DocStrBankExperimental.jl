```
Kucoin.list_accounts(api_data[; currency[, type]]) -> JSON3.Array{JSON3.Object}
```

アカウントのリストを取得します。詳細については、Kucoinの公式[ドキュメント](https://docs.kucoin.com/#list-accounts)を参照してください。

# 引数

  * `api_data::UserApiData`: APIキー、シークレット、パスフレーズなどのユーザーAPIデータを保持します。

# キーワード

  * `currency::String`: [オプション] ユニークな通貨のKucoinコード
  * `type::String`: [オプション] アカウントタイプ、有効な値は `"main"`、`"trade"`、`"margin"` または `"pool"` です。

# 戻り値

  * `JSON3.Array{JSON3.Object}`

```json
[
  {
    "id": "5bd6e9286d99522a52e458de",  //accountId
    "currency": "BTC",  //通貨
    "type": "main",  //アカウントタイプ、メインとトレードを含む
    "balance": "237582.04299",  //通貨の総資産
    "available": "237582.032",  //通貨の利用可能資産
    "holds": "0.01099"  //通貨の保有資産
  },
  {
    "id": "5bd6e9216d99522a52e458d6",
    "currency": "BTC",
    "type": "trade",
    "balance": "1234356",
    "available": "1234356",
    "holds": "0"
}]
```
