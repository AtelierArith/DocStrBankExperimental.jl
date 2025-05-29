```
listtokens(client::PCloudClient; kwargs...)
```

現在のユーザーに関連付けられた現在アクティブなトークンのリストを取得します。

ソース: https://docs.pcloud.com/methods/auth/listtokens.html

# 出力

トークン情報が満載のオブジェクトのリスト `tokens` を返します。各オブジェクトには以下のフィールドがあります：

  * `tokenid::Int`: トークンの識別番号。
  * `device::String`: トークンが与えられたデバイスに関する情報。
  * `created::datetime`: トークンが作成された日時。
  * `expires_inactive::datetime`: 所有者が使用しない場合、トークンが期限切れになる日時。
  * `expires::datetime`: トークンが期限切れになる日時。これはトークンがアクティブである最後の瞬間です。

# 出力例

```
{
    "result": 0,
    "tokens": [
        {
            "tokenid": 163409641,
            "device": "ユーザーエージェント情報",
            "created": "Mon, 09 Jun 2014 10:24:51 +0000"
            "expires_inactive": "Thu, 10 Jul 2014 10:24:51 +0000",
            "expires": "Tue, 09 Jun 2015 10:24:51 +0000",
        },

        ...

    ]    
}
```
