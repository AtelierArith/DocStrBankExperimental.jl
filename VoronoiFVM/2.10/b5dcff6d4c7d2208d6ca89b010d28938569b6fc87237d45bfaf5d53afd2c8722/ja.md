```julia
mutable struct TransientSolverHistory <: AbstractVector{VoronoiFVM.NewtonSolverHistory}
```

過渡解/パラメータ埋め込みのための履歴情報

抽象ベクターとして、各暗黙のオイラー/埋め込みステップの履歴を提供します。情報を抽出する他の方法については、[`summary`](@ref)および[`details`](@ref)を参照してください。

  * `histories::Any`:  各暗黙のオイラー・ニュートン反復の履歴
  * `times::Any`:  時間値
  * `updates::Any`:  ステップ制御に使用される更新ノルム
