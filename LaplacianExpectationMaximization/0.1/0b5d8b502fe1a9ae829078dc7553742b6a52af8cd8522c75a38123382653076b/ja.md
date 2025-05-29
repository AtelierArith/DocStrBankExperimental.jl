```
OptimisersOptimizer(opt; maxeval = 10^5, maxtime = Inf, min_grad_norm = 1e-8, lower_bounds = -Inf, upper_bounds = Inf)
```

Optimizer `opt` は `subtypes(Optimisers.AbstractRule)` のいずれかであることができます。最適化は、勾配のL2ノルムが `min_grad_norm` を下回るか、`maxeval` または `maxtime` に達したときに停止します。詳細は [Optimisers](https://fluxml.ai/Optimisers.jl/dev/api/) を参照してください。
