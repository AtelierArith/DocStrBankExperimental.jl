```
linpred(p::LinPred, f::Real=1.0)
```

線形予測子 `p.X * (p.beta0 .+ f * p.delbeta)` を返します。
