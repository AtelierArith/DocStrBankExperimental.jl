```
rand(rng::AbstractRNG, p::Function, s::Walker2014Sampler, x0::Int)
```

ターゲットの非正規化確率密度関数 `p` を使用して、サンプラー `s` で MCMC の次の状態を `x0` を現在の状態と仮定して描画します。`rng` と `s` の両方はこのプロセスで変更されます。
