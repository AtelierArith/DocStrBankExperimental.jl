```
steady_force(q,panels,U=SVector(-1,0,0);kwargs...)
```

統合された圧力力係数 Cₚ =∫ₛ cₚ n da の `panels` の強さ `q`。ここで cₚ = 1-u²/U²、`U` は自由流速度で、u=U+∇Φ は流れの速度です。計算は `Threads.nthreads()>1` の場合にマルチスレッドで加速されます。
