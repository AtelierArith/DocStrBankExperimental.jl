```
function isshutdown(process::Supervised)
```

プロセスの受信ボックスにシャットダウンコマンドがある場合は `true` を返します。

副作用として、`shutdown` リクエストが見つかるまでプロセスの受信ボックスからメッセージを削除します。
