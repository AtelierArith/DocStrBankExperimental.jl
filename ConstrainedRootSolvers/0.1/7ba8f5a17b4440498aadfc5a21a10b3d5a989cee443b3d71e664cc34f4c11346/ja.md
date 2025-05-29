2Dおよびそれ以上の根解法のための減少ステップ法。この方法は、改善が見られなくなるまで初期推定の各変数を増加または減少させます。その後、増分ステップが減少し、根解法が続行されます。

```julia
mutable struct ReduceStepMethodND{FT<:AbstractFloat} <: ConstrainedRootSolvers.AbstractCRSMethod{FT<:AbstractFloat}
```

# フィールド

  * `x_mins::Vector{FT} where FT<:AbstractFloat`: 下限
  * `x_maxs::Vector{FT} where FT<:AbstractFloat`: 上限
  * `x_inis::Vector{FT} where FT<:AbstractFloat`: 初期推定
  * `x_targ::Vector{FT} where FT<:AbstractFloat`: 目標x
  * `x_temp::Vector{FT} where FT<:AbstractFloat`: 一時的なx
  * `Δ_inis::Vector{FT} where FT<:AbstractFloat`: 初期ステップ
  * `Δ_oper::Vector{FT} where FT<:AbstractFloat`: 操作ステップ
  * `Δjd::Vector{Bool}`: 判定のベクター
