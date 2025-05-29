```
Prometheus.inc(counter::Counter, v::Real = 1)
```

Increment the value of the counter with `v`. The value defaults to `v = 1`.

Throw a `Prometheus.ArgumentError` if `v < 0` (a counter must not decrease).
