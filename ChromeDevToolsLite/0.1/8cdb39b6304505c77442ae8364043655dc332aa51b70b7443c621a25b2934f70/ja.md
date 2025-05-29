```
connect!(client::WSClient; max_retries::Int = MAX_RETRIES,
    retry_delay::Real = RETRY_DELAY,  timeout::Real = CONNECTION_TIMEOUT, verbose::Bool = false)
```

Chrome DevTools Protocol WebSocketエンドポイントに接続します。接続されたクライアントを返します。

# 引数

  * `max_retries::Int`: 接続を確立するための最大再試行回数。
  * `retry_delay::Real`: 再試行間の遅延（秒単位）。
  * `timeout::Real`: 接続のタイムアウト（秒単位）。
  * `verbose::Bool`: 詳細なデバッグ情報を表示するかどうか。
