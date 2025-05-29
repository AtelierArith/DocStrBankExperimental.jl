```
try_connect(client::WSClient; max_retries::Int = MAX_RETRIES,
    retry_delay::Real = RETRY_DELAY, timeout::Real = CONNECTION_TIMEOUT,
    verbose::Bool = false)
    retry_delay::Real = RETRY_DELAY, verbose::Bool = false)
```

WebSocket接続を確立し、リトライロジックとタイムアウトを設定します。
