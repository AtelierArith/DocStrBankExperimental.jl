```
size_p1g(; <keyword arguments>)
```

グループ1対母集団の比率に必要なサンプルサイズを計算します。

# 引数

  * `p1::Float64`: 母集団の比率
  * `p2::Float64`: 研究グループの比率
  * `alpha::Float64=0.05`: 第I種過誤の確率
  * `power::Float64=0.8`: グループ間の差を検出する能力（power = 1 - beta、ここでbetaは第II種過誤の確率）

# 戻り値

  * `n::Int64`: グループ1のサンプルサイズ
