```julia
mutable struct NewtonSolverHistory <: AbstractVector{Float64}
```

非線形システムの1回のニュートン解法の履歴情報。抽象ベクトルとして、更新ノルムの履歴を提供します。情報を抽出する他の方法については、[`summary`](@ref)および[`details`](@ref)を参照してください。

  * `nlu::Int64`:  ジャコビ行列の因子分解の数  デフォルト: 0
  * `nlin::Int64`:  線形反復ステップ/因子分解解の数  デフォルト: 0
  * `time::Float64`:  解法の経過時間  デフォルト: 0.0
  * `updatenorm::Any`:  $||u_{i+1}-u_i||$ のノルムの履歴  デフォルト: zeros(0)
  * `l1normdiff::Any`:  $|\;||u_{i+1}||_1 - ||u_{i}||_1\;|/ ||u_{i}||_1$ のノルムの履歴  デフォルト: zeros(0)
