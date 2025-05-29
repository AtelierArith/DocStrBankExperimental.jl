```
gridscore_lb(Xtrain, Ytrain, X, Y; algo, score, pars = nothing, 
    lb, verbose = false)
```

`gridscore` のための作業関数。

リッジ正則化を使用するモデル（例：RR）に対して特定かつ高速です。引数 `pars` には `lb` を含めてはいけません。

例については関数 `gridscore` を参照してください。
