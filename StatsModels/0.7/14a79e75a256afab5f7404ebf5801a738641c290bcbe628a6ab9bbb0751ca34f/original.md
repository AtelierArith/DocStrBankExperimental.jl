```
ModelMatrix(mf::ModelFrame)
```

Convert a `ModelFrame` into a numeric matrix suitable for modeling

# Fields

  * `m::AbstractMatrix{<:AbstractFloat}`: the generated numeric matrix
  * `assign::Vector{Int}` the index of the term corresponding to each column of `m`.

# Constructors

```julia
ModelMatrix(mf::ModelFrame)
# Specify the type of the resulting matrix (default Matrix{Float64})
ModelMatrix{T <: AbstractMatrix{<:AbstractFloat}}(mf::ModelFrame)
```
