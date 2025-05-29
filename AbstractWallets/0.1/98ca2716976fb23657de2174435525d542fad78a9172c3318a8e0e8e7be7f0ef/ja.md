```
build_send_transaction(source::AbstractWallet, target, asset, quantity;
                       fulfill_maximum=false)
```

指定された `asset` の一定量を `target` に送信するトランザクションを準備します。これは、元の `wallet` にこの `quantity` が含まれている場合に行われます。`fulfill_maximum` が `true` の場合、トランザクションを可能な限り満たします。
