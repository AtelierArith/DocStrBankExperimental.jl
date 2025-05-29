```
mcmc_ising2d!(; s=rand_ising2d(), k=1.0, β=k*β_ising2d, rng=default_rng(),
    algorithm=default_algorithm(), progress=true, 
    nwarmups=1000, nskips=100, niters=5000
)
```

は、長さ niters のマルコフ連鎖モンテカルロシミュレーションの結果を返します。これは、2D イジングモデルの状態の配列です。
