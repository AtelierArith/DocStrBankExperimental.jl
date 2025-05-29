```
cuhre(integrand, ndim=2, ncomp=1[, keywords]) -> integral, error, probability, neval, fail, nregions
```

`integrand`の単位ハイパーキューブにおける積分を`ndim`次元でCuhreアルゴリズムを使用して計算します。 `integrand`は`ncomp`コンポーネントを持つベクトル関数です。 `ncomp`はデフォルトで1、`ndim`はデフォルトで2で、2以上でなければなりません。

受け入れられるキーワード:

  * `userdata`
  * `nvec`
  * `rtol`
  * `atol`
  * `flags`
  * `minevals`
  * `maxevals`
  * `key`
  * `statefile`
  * `spin`
