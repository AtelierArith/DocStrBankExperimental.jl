```
summary(x, y)
```

要約統計量を返します。

# 引数

  * `x::AbstractVector`
  * `y::AbstractVector`
  * `g1::String="1"`: グループ1の名前
  * `g2::String="2"`: グループ2の名前

# 戻り値

名前付きタプルを含む:

  * `mm1::Float64`: 平均
  * `mm2::Float64`: 平均
  * `v1::Float64`: 分散
  * `v2::Float64`: 分散
  * `s1::Float64`: 標準偏差
  * `s2::Float64`: 標準偏差
  * `me1::Float64`: 中央値
  * `me2::Float64`: 中央値
  * `mo1::Float64`: 最頻値
  * `mo2::Float64`: 最頻値
