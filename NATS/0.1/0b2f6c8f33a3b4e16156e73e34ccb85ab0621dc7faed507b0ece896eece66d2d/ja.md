```julia
request(connection, nreplies, subject; ...)
request(connection, nreplies, subject, data; timer)

```

複数の返信を要求します。`nreplies` 返信を受信するか、タイマーが期限切れになると、メッセージのベクターが返されます。指定された数よりも少ないメッセージが返される場合があります（タイムアウトが発生した場合は空の配列もあり）、エラーはフィルタリングされません。

オプションのキーワード引数は次のとおりです：

  * `timer`: `timer` が期限切れになるまで返信が受信されなかった場合、空のベクターが返されます

# 例

```julia-repl
julia> request(connection, 2, "help.please"; timer = Timer(0))
NATS.Msg[]
```
