```
build_destroy_transaction(wallet::AbstractWallet, asset, quantity;
                          fulfill_maximum=false)
```

指定された `asset` の一定量を元の `wallet` に含まれている場合に破棄するトランザクションを準備します。`fulfill_maximum` が `true` の場合、トランザクションを可能な限り満たします。
