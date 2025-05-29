```
matmul!(C, A, B[, α, β, max_threads])
```

Calculates `C = α * A * B + β * C` in place, overwriting the contents of `C`. It may use up to `max_threads` threads. It will not use threads when nested in other threaded code.
