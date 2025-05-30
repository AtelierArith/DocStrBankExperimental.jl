```
univariate_unimodal_HDR(d::UnivariateDistribution, region::Real, num_steps::Int)
```

単変量の単峰分布の最高密度領域（HDR）を見つけるためのグリッドベースのアプローチ。見つかったHDR区間を長さ2のベクターとして返します。

# 引数

  * `d`: [Distributions.jl](https://juliastats.org/Distributions.jl/stable/) で定義された `UnivariateDistribution`。
  * `region`: `d` の最高密度領域の密度の割合を指定する実数 ∈ [0, 1]。
  * `num_steps`: 左側と右側のブラケットの間を線形に分割するステップ数で、含む。ここで `l=0.0` および `r=1.0-region`。これらのステップで、下位および上位の分位数が `region` 離れて計算されます。これらのステップでの下位および上位の分位数の間の最小距離を持つものがHDRとして推定されます。`num_steps` は、対称分布での正確な精度を許可するために、少なくとも3かつ奇数である必要があります。
