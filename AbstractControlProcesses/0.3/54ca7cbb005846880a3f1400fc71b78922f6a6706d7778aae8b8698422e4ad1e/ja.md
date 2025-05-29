```
control(P::AbstractProcess, u)
```

制御信号 `u` をプロセスに送信します。ここで、`u` は次元 `num_inputs(P)` を持つ必要があります。
