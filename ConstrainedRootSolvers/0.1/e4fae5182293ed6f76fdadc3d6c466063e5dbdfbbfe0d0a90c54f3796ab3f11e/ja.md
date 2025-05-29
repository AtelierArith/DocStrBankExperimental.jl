Nelder-Mead法による2Dおよびそれ以上のソルバー

```julia
mutable struct NelderMeadMethod{FT<:AbstractFloat} <: ConstrainedRootSolvers.AbstractCRSMethod{FT<:AbstractFloat}
```

# フィールド

  * `N::Int64`: 最適化するパラメータの数
  * `x_inis::Vector{FT} where FT<:AbstractFloat`: 初期値
  * `simplex::Array{Vector{FT}, 1} where FT<:AbstractFloat`: 次元(N+1) * (N+1)のベクトルの単体
  * `cen_x::Vector{FT} where FT<:AbstractFloat`: セントロイド
  * `ref_x::Vector{FT} where FT<:AbstractFloat`: 反射
  * `exp_x::Vector{FT} where FT<:AbstractFloat`: 拡張
  * `con_x::Vector{FT} where FT<:AbstractFloat`: 縮小
  * `history::Array{Vector{FT}, 1} where FT<:AbstractFloat`: すべてのシミュレーションの履歴
