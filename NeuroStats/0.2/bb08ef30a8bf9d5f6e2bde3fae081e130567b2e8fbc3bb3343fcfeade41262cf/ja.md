```
ba(x, y; <キーワード引数>)
```

2つの臨床測定値のBland-Altman比較を計算します。

# 引数

  * `x::AbstractVector`
  * `y::AbstractVector`
  * `la::FLoat64=0.95`: 各比較の95%同意限界（平均差 ± 1.96標準偏差）

# 戻り値

  * `m::Float64`: 平均差
  * `s_u::Float64`: +1.96（デフォルトのlaの場合）差の標準偏差
  * `s_d::Float64`: -1.96（デフォルトのlaの場合）差の標準偏差

# 注意事項

Bland-Altmanプロットを描画するには: `p = hline([0, m]); hline!([0, s_u]); hline!([0, s-d])`
