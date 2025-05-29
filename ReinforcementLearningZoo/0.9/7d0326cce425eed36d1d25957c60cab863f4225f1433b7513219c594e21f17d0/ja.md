```
ImplicitQuantileNet(;ψ, ϕ, header)
```

```
        quantiles (n_action, n_quantiles, batchsize)
           ↑
         header
           ↑
feature ↱  ⨀   ↰ transformed embedding
       ψ       ϕ
       ↑       ↑
       s        τ
```
