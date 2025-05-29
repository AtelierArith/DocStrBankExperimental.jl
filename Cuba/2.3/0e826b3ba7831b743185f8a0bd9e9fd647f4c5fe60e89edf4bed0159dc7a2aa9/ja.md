```
vegas(integrand, ndim=1, ncomp=1[, keywords]) -> integral, error, probability, neval, fail, nregions
```

`integrand`の単位ハイパーキューブにおける積分を`ndim`次元でVegasアルゴリズムを使用して計算します。`integrand`は`ncomp`成分を持つベクトル関数です。`ndim`と`ncomp`のデフォルトは1です。

受け入れられるキーワード:

  * `userdata`
  * `nvec`
  * `rtol`
  * `atol`
  * `flags`
  * `seed`
  * `minevals`
  * `maxevals`
  * `nstart`
  * `nincrease`
  * `nbatch`
  * `gridno`
  * `statefile`
  * `spin`
