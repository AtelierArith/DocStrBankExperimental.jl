```
computeDelta!(p::QuadraticEigenvalueProblem{N,T}, c::AIMCache{N,Polynomial{T}}) where {N <: Unsigned, T <: Number}
```

AIMの「量子化条件」を計算して返します。

# 入力

  * `m::AIMSteppingMethod`: 使用するステッピングメソッド。
  * `p::QuadraticEigenvalueProblem`: 二次周波数問題。
  * `c::AIMCache`: pから作成されたAIMキャッシュオブジェクト。

# 出力

問題の固有値の根を持つ`Polynomial{T}`型のオブジェクト。
