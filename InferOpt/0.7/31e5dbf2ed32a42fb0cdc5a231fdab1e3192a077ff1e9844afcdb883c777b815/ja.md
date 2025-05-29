```
soft_sort(θ::AbstractVector; ε=1.0, rev::Bool=false, regularization=:l2)
```

ベクトルθの高速微分可能ソート。

# 引数

  * `θ`: ソートするベクトル

# キーワード（オプション）引数

  * `ε::Float64=1.0`: 正則化のサイズ
  * `rev::Bool=false`: falseの場合は昇順にソート
  * `regularization=:l2`: :l2の場合はl2正則化を使用し、:klの場合はkl正則化を使用

[`soft_sort_l2`](@ref)および[`soft_sort_kl`](@ref)も参照してください。
