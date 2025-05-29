```
AbstractGradientSolverState <: AbstractManoptSolverState
```

勾配ベースのオプションデータ用の一般的な [`AbstractManoptSolverState`](@ref) タイプです。

これは以下を仮定します。

  * 反復はフィールド `p` に保存されます。
  * `p` における勾配は `X` に保存されます。

# 参照

[`GradientDescentState`](@ref), [`StochasticGradientDescentState`](@ref), [`SubGradientMethodState`](@ref), [`QuasiNewtonState`](@ref).
