```
critfunc(s, θ, rho; penalizediag=true)
```

グラフィカルラッソの目的関数の値を計算します。

# 引数

  * `s::AbstractMatrix`: 統計的共分散行列。
  * `θ::AbstractMatrix`: 精度行列。
  * `rho::Real`: 正則化パラメータ。
  * `penalizediag::Bool=true`: 対角成分にペナルティを課すかどうか。 (オプション)

# 戻り値

  * `Real`: 目的関数の値。
