```
linpred(p::LinPred, f::Real=1.0)
```

Return the linear predictor `p.X * (p.beta0 .+ f * p.delbeta)`
