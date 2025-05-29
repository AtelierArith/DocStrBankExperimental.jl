```
gridcv_lb(X, Y; segm, algo, score, pars = nothing, lb, verbose = false)
```

`gridcv`のための作業関数。

リッジ正則化を使用するモデル（例：RR）に対して、`gridcv_br`よりも特定的で高速です。引数`pars`には`nlv`を含めてはいけません。

例については関数`gridcv`を参照してください。
