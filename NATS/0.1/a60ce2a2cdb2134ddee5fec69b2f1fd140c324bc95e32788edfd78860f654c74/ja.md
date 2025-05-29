```julia
request(connection, subject; ...)
request(connection, subject, data; timer)

```

NATS [リクエスト-返信](https://docs.nats.io/nats-concepts/core-nats/reqreply) メッセージを送信します。

デフォルトのタイムアウトは5.0秒で、`timer`を渡すことで上書きできます。これは、`NATS_REQUEST_TIMEOUT_SECONDS` 環境変数でグローバルに設定できます。

オプションのキーワード引数は次のとおりです：

  * `timer`: `timer`が期限切れになるまでに返信が受信されない場合、エラーが発生します。

# 例

```julia-repl
julia> NATS.request(connection, "help.please")
NATS.Msg("l9dKWs86", "7Nsv5SZs", nothing, "", "OK, I CAN HELP!!!")

julia> request(connection, "help.please"; timer = Timer(0))
ERROR: No replies received.
```
