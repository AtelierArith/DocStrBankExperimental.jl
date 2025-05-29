```
gumbelfitbayes(model::BlockMaxima{Gumbel};
    niter::Int=5000,
    warmup::Int=2000)
```

`BlockMaxima`モデルパラメータの事後分布からサンプルを生成します。
