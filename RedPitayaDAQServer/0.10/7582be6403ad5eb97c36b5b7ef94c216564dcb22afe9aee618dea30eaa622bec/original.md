```
query(rp::RedPitaya, cmd, T::Type [timeout = 5.0, N = 100])
```

Send a query to the RedPitaya. Parse reply as `T`.

Waits for `timeout` seconds and checks every `timeout/N` seconds.
