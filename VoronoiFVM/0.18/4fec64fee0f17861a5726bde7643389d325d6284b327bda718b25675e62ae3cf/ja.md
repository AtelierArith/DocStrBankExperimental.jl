```julia
mutable struct TransientSolverHistory <: AbstractVector{VoronoiFVM.NewtonSolverHistory}
```

過渡解/パラメータ埋め込みのための履歴情報

抽象ベクトルとして、各暗黙のオイラー/埋め込みステップの履歴を提供します。情報を抽出する他の方法については、[`summary`](@ref)および[`details`](@ref)を参照してください。

  * `histories::Any`:  各暗黙のオイラー・ニュートン反復の履歴  デフォルト: Vector{NewtonSolverHistory}(undef, 0)
  * `times::Any`:  時間値  デフォルト: zeros(0)
  * `updates::Any`:  ステップ制御に使用される更新ノルム  デフォルト: zeros(0)
