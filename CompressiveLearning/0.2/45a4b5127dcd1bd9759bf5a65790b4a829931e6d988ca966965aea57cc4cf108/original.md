```julia
struct QuantizedFourierSkOp{T<:AbstractMatrix{Float64}, U<:Union{Nothing, Vector{Float64}}} <: CompressiveLearning.LinearSkOp
```

# Fields

  * `m::Int64`
  * `d::Int64`
  * `Ω::AbstractMatrix{Float64}`
  * `ξ::Union{Nothing, Vector{Float64}}`
