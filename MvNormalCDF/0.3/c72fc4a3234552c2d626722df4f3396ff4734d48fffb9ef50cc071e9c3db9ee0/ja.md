```
mvnormcdf(dist::MvNormal, a, b; m::Integer = 1000*size(dist.Σ,1), rng = RandomDevice())
```

多変量正規確率積分を、m点の準モンテカルロアルゴリズムを使用して計算します（多変量正規分布については [MvNormal](https://juliastats.org/Distributions.jl/stable/multivariate/#Distributions.MvNormal) を参照）。

確率 p は誤差推定 e と共に出力されます。

# 引数

  * `dist::MvNormal`: Distributions.jl からの多変量正規分布
  * `a::AbstractVector`: 下限積分制限の列ベクトル
  * `b::AbstractVector`: 上限積分制限の列ベクトル
  * `m::Integer`:        積分点の数（デフォルトは 1000*次元）
  * `rng`: 擬似乱数生成器

# 参考文献

  * Genz, A. (1992). 多変量正規確率の数値計算. Journal of Computational and Graphical Statistics, 1, 141–150
  * Genz, A. (1993). 多変量正規確率の計算方法の比較. Computing Science and Statistics, 25, 400–405
