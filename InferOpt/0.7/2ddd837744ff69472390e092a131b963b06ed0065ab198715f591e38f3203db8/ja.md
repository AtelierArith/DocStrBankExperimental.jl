```
SoftSort(; ε::Float64=1.0, rev::Bool=false, is_l2_regularized::Bool=true)
```

[`SoftSort`](@ref)のコンストラクタ。

# 引数

  * `ε::Float64=1.0`: 正則化のサイズ
  * `rev::Bool=false`: falseの場合は昇順にソート
  * `is_l2_regularized::Bool=true`: trueの場合はl2正則化を使用し、それ以外はkl正則化を使用
