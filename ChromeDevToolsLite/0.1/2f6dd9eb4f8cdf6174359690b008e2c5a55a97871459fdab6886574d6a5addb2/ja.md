```
wait_for_ready_state(client::WSClient; retry_delay::Real = 0.3,
    timeout::Real = 10)
```

ドキュメントの準備状態が完了するのを待ちます。タイムアウトに達した場合は、TimeoutErrorをスローします。
