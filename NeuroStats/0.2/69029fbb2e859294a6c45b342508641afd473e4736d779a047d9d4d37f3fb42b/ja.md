```
size_c1diff(; <keyword arguments>)
```

連続変数の差を検出するための必要なサンプルサイズを計算します（グループ1対母集団）。

# 引数

  * `s1::Real`: 検出したい研究の標準偏差
  * `s2::Real`: 母集団の標準偏差
  * `twotailed::Bool=true`: trueの場合、推定は二尾差のためのもの
  * `power::Float64=0.8`: グループ間の差を検出する能力（`power = 1 - beta`、ここで`beta`はタイプIIエラーの確率）

# 戻り値

  * `n::Int64`: 研究のサンプルサイズ
