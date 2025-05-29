```
KdbConnectionInfo(host::String, port::Integer[, user::String, timeout::Integer])
```

KDB接続の情報。`host`と`port`が必要です。`user`と`timeout`はオプションです。`timeout`はクエリタイムアウトまでのミリ秒を表す整数です。

`open(conn::KdbConnectionInfo)`を使用して接続を開きます。
