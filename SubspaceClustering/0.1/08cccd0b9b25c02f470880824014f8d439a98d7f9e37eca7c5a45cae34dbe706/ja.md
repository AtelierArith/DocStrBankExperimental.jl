```
KSSResult{
    TU<:AbstractVector{<:AbstractMatrix{<:AbstractFloat}},
    Tc<:AbstractVector{<:Integer},
    T<:Real}
```

[`kss`](@ref) の出力。

# フィールド

  * `U::TU`: サブスペース基底行列のベクトル `U[1],...,U[K]`
  * `c::Tc`: クラスタ割り当てのベクトル `c[1],...,c[N]`
  * `iterations::Int`: 実行された反復の数
  * `totalcost::T`: 総コスト関数の最終値
  * `counts::Vector{Int}`: クラスタサイズのベクトル `counts[1],...,counts[K]`
  * `converged::Bool`: 最終収束状態
