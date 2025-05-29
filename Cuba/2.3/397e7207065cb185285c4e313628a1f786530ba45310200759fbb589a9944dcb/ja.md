```
divonne(integrand, ndim=2, ncomp=1[, keywords]) -> integral, error, probability, neval, fail, nregions
```

`integrand`の単位ハイパーキューブ上での積分を`ndim`次元でDivonneアルゴリズムを使用して計算します。 `integrand`は`ncomp`コンポーネントを持つベクトル関数です。 `ncomp`のデフォルトは1、`ndim`のデフォルトは2で、2以上でなければなりません。

受け入れられるキーワード:

  * `userdata`
  * `nvec`
  * `rtol`
  * `atol`
  * `flags`
  * `seed`
  * `minevals`
  * `maxevals`
  * `key1`
  * `key2`
  * `key3`
  * `maxpass`
  * `border`
  * `maxchisq`
  * `mindeviation`
  * `ngiven`
  * `ldxgiven`
  * `xgiven`
  * `nextra`
  * `peakfinder`
  * `statefile`
  * `spin`
