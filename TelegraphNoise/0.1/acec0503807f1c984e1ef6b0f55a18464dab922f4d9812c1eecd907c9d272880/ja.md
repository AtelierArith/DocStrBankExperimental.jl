```
generate_telegraph([rng = default_rng()], dwell_time, signal_length; amplitude = one(T) ) → Telegraph
```

指定された `dwell_time` と与えられた長さ `signal_length` のランダムな [`Telegraph`](@ref) 信号を初期化する関数です。
