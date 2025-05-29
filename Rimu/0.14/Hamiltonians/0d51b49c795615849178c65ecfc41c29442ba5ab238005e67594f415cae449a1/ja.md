```
ExtendedHubbardReal1D(address; u=1.0, v=1.0, t=1.0, boundary_condition=:periodic)
```

1次元チェーン上の拡張ハバードモデルを実装します。このハミルトニアンは、`boundary_condition`の選択に応じて、実数または複素数のいずれかになります。

$$
\hat{H} = -t \sum_{\langle i,j\rangle} a_i^† a_j + \frac{u}{2}\sum_i n_i (n_i-1) +
v \sum_{\langle i,j\rangle} n_i n_j
$$

# 引数

  * `address`: 開始アドレス。
  * `u`: オンサイト相互作用パラメータ
  * `v`: 次近隣相互作用
  * `t`: ホッピング強度
  * `boundary_condition` 次の値がサポートされています：

      * `:periodic`: リング幾何学を実現する通常の周期境界条件。
      * `:hard_wall`: 境界を越えるホッピングは許可されていません。
      * `:twisted`: `:periodic`のようですが、境界を越えるホッピングには追加の因子`-1`がかかります。
      * `θ <: Number`: `:periodic`および`:twisted`のようですが、境界を越えるホッピングには右へのホップに対して因子$\exp(iθ)$、左へのホップに対して因子$\exp(−iθ)$がかかります。この選択により、ハミルトニアンは複素数の`eltype`を持ち、それ以外の場合は`eltype`はパラメータ`t`、`u`、`v`の型によって決まります。

[`HubbardRealSpace`](@ref)も参照してください。
