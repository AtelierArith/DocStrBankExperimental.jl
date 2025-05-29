```julia
unsubscribe(connection, sub; max_msgs)

```

サブジェクトからの購読を解除します。`sub`は`subscribe`または`reply`から返されるオブジェクトです。

オプションのキーワード引数は次のとおりです：

  * `max_msgs`: サーバーが`unsubscribe`メッセージを受信した後に送信する最大メッセージ数。これは、しばらくの時間遅延の後に発生する可能性があります。
