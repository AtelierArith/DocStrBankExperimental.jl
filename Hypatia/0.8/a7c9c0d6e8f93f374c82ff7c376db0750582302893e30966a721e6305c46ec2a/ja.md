```julia
struct PosSemidefTriSparseCone{I<:Hypatia.Cones.PSDSparseImpl, T<:Real, R<:Union{Complex{T<:Real}, T<:Real}} <: MathOptInterface.AbstractVectorSet
```

See [`Cones.PosSemidefTriSparse`](@ref).

  * `side::Int64`
  * `row_idxs::Vector{Int64}`
  * `col_idxs::Vector{Int64}`
  * `use_dual::Bool`
