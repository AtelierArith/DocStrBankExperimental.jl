```
wait_until_done(ctx::Context, rsp::TransactionResponse) -> TransactionResponse
wait_until_done(ctx::Context, transaction) -> TransactionResponse
wait_until_done(ctx::Context, txn_id::String) -> TransactionResponse
```

`transaction`が端末状態に達するまでブロックし、レスポンスを返します。

トランザクションが終了するまで、get_transaction()を継続的にポーリングしてトランザクションの状態を確認します。トランザクションは、`COMPLETED`または`ABORTED`のいずれかの端末状態に達した時点で終了します。ポーリングは、ネットワークトラフィックを過負荷にしないように、低遅延の結果を確保するために低オーバーヘッドの指数バックオフを使用します。
