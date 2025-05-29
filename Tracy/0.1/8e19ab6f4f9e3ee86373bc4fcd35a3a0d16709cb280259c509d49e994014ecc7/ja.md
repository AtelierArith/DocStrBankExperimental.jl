```
wait_for_tracy(;timeout::Float64 = 20.0)
```

`libtracy` がリスニングキャプチャエージェントに接続するまで最大 `timeout` 秒待機します。タイムアウトが発生した場合、`InvalidStateException` をスローします。
