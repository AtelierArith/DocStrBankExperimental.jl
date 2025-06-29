```julia
reconnect(connection; should_wait)

```

接続を再接続します。接続が `CONNECTED` の場合、これにより接続が閉じられ、再度オープンされ、すべての既存のサブスクリプションが再登録されます。接続が `DISCONNECTED` の場合、以前のすべてのサブスクリプションが復元された状態で接続を試みます。接続がすでに `CONNECTING` の場合、このメソッドは効果がありません。接続が `DRAINING` または `DRAINED` の場合に呼び出されると、エラーが発生します。

再接続期間中に、接続によって公開されたメッセージと受信されたメッセージの一部が失われる可能性があります。

オプションのキーワード引数：

  * `should_wait`: `true` の場合、メソッドは再接続プロセスが開始されるまでブロックします。デフォルトは `true` です。
