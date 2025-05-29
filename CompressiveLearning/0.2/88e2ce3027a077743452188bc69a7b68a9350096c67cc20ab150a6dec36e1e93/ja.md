```julia
struct FourierSkOp{T<:AbstractMatrix{Float64}, U<:Union{Nothing, Vector{Float64}}} <: CompressiveLearning.LinearSkOp
```

# フィールド

  * `m::Int64`: スケッチサイズ
  * `d::Int64`: 次元
  * `Ω::AbstractMatrix{Float64}`: 周波数ベクトルの行列（列）
  * `ξ::Union{Nothing, Vector{Float64}}`: ディザリングベクトル。スケッチは $exp.(i(Ωᵀx + ξ))$ として計算されます、$ξ≠0$ の場合。
