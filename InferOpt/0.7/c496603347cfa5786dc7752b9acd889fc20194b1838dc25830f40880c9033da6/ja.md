```
SoftRank(; ε::Float64=1.0, rev::Bool=false, is_l2_regularized::Bool=true)
```

[`SoftRank`](@ref)のコンストラクタ。

# 引数

  * `ε::Float64=1.0`: 正則化のサイズ
  * `rev::Bool=false`: falseの場合は昇順でランク付け
  * `regularization="l2"`: 使用される正則化、"l2"または"kl"のいずれか
