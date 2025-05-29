```
computeDelta!(m::AIMSteppingMethod, p::NumericAIMProblem{N,T}, c::AIMCache{N,T}, ω::T) where {N <: Unsigned, T <: Number}
```

AIMの「量子化条件」を計算して返します。

# 入力

  * `m::AIMSteppingMethod`: 使用するステッピングメソッド。
  * `p::QuadraticEigenvalueProblem`: 二次周波数問題。
  * `c::AIMCache`: pから作成されたAIMキャッシュオブジェクト。
  * `ω::T`: 量子化条件を評価する点。

# 出力

点ωにおけるAIM量子化条件を表す型`T`のオブジェクト。
