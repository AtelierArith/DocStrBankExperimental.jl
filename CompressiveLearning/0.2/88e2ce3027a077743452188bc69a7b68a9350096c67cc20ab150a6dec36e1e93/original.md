```julia
struct FourierSkOp{T<:AbstractMatrix{Float64}, U<:Union{Nothing, Vector{Float64}}} <: CompressiveLearning.LinearSkOp
```

# Fields

  * `m::Int64`: Sketch size
  * `d::Int64`: Dimension
  * `Ω::AbstractMatrix{Float64}`: Matrix of frequency vectors (columns)
  * `ξ::Union{Nothing, Vector{Float64}}`: Dithering Vector. The sketch is computed as $exp.(i(Ωᵀx + ξ))$ when $ξ≠0$.
