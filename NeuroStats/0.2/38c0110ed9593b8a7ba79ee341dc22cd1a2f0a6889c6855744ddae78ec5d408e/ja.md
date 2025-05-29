```
cmp_stat(stat_dist, v)
```

与えられた統計値の下または上にある要素の割合を計算します。

# 引数

  * `stat_dist::AbstractVector`: 統計値の分布
  * `v::Real`: 統計値
  * `type::Symbol=:g`: `v` より大きい要素（`:g`）または小さい要素（`:l`）の割合を計算

# 戻り値

  * `p::Float64`
