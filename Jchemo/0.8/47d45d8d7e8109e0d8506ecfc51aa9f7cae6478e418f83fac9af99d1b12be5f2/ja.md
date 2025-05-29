```
gridcv_lv((X, Y; segm, algo, score, pars = nothing, nlv, verbose = false)
```

`gridcv`のための作業関数。

潜在変数を使用するモデル（例：PLSR）に対して、特定かつ高速です。引数`pars`には`nlv`を含めてはいけません。

例については関数`gridcv`を参照してください。
