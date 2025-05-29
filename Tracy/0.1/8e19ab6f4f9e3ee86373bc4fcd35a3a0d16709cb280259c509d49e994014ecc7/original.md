```
wait_for_tracy(;timeout::Float64 = 20.0)
```

Waits up to `timeout` seconds for `libtracy` to connect to a listening capture agent.  If a timeout occurs, throws an `InvalidStateException`.
