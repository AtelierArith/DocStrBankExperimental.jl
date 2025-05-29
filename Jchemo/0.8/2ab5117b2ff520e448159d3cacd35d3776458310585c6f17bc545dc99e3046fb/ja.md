```
gridscore_lv(Xtrain, Ytrain, X, Y; algo, score, pars = nothing, 
    nlv, verbose = false)
```

`gridscore`のための作業関数。

潜在変数を使用するモデル（例：PLSR）に対して特定かつ高速です。引数`pars`には`nlv`を含めてはいけません。

例については関数`gridscore`を参照してください。
