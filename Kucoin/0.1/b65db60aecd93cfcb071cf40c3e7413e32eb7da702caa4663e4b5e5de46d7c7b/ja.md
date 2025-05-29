Kucoin.get*ws*token([api_data]) -> JSON3.Object

ウェブソケット接続トークンを申請します。詳細についてはKucoinの公式[docs](https://docs.kucoin.com/#apply-connect-token)を参照してください。

# 引数

  * `api_data::UserApiData`: [オプション] APIキー、シークレット、パスフレーズなどのAPIデータを保持します。

欠如している場合は、パブリックチャネルでのみ使用できるトークンを返します。

# 戻り値

  * `JSON3.Object`

```json
{
  "instanceServers": [
    {
      "endpoint": "wss://push1-v2.kucoin.com/endpoint",
      "protocol": "websocket",
      "encrypt": true,
      "pingInterval": 50000,
      "pingTimeout": 10000
    }
  ],
  "token": "vYNlCtbz4XNJ1QncwWilJnBtmmfe4geLQDUA62kK=="
}
```
