```julia
struct SqRandomSkOp{T<:AbstractMatrix{Float64}} <: CompressiveLearning.LinearSkOp
```

Base type for non-composite sketching operators.

# Fields

  * `m::Int64`
  * `d::Int64`
  * `Ω::AbstractMatrix{Float64}`
