```julia
struct SqRandomSkOp{T<:AbstractMatrix{Float64}} <: CompressiveLearning.LinearSkOp
```

非複合スケッチング演算子のベースタイプです。

# フィールド

  * `m::Int64`
  * `d::Int64`
  * `Ω::AbstractMatrix{Float64}`
