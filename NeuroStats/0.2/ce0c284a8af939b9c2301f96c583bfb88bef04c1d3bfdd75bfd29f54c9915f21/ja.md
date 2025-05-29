```
size_c1g(; <keyword arguments>)
```

連続変数の必要サンプルサイズを計算します（グループ1対母集団）。

# 引数

  * `m::Real`: 母集団の平均
  * `s::Real`: 母集団の標準偏差
  * `xbar::Real`: 研究グループの平均
  * `alpha::Float64=0.05`: 第一種過誤の確率
  * `power::Float64=0.8`: グループ間の差を検出する能力（power = 1 - beta、ここでbetaは第二種過誤の確率）
  * `iter::Bool=false`: 反復法を使用する

# 戻り値

  * `n::Int64`: グループのサンプルサイズ
