```
query(rp::RedPitaya, cmd [, timeout = 5.0, N = 100])
```

Send a query to the RedPitaya command socket. Return reply as String.

Waits for `timeout` seconds and checks every `timeout/N` seconds.

See also [receive](@ref).
