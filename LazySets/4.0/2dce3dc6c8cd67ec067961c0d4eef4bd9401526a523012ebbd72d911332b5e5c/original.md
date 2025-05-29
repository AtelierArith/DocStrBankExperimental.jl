```
Projection(X::LazySet{N}, variables::AbstractVector{Int}) where {N}
```

Return a lazy projection of a set.

### Input

  * `X`         – set
  * `variables` – variables of interest

### Output

A lazy `LinearMap` that corresponds to projecting `X` along the given variables `variables`.

### Examples

The projection of a three-dimensional cube into the first two coordinates:

```jldoctest Projection
julia> B = BallInf([1.0, 2, 3], 1.0)
BallInf{Float64, Vector{Float64}}([1.0, 2.0, 3.0], 1.0)

julia> Bproj = Projection(B, [1, 2])
LinearMap{Float64, BallInf{Float64, Vector{Float64}}, Float64, SparseArrays.SparseMatrixCSC{Float64, Int64}}(sparse([1, 2], [1, 2], [1.0, 1.0], 2, 3), BallInf{Float64, Vector{Float64}}([1.0, 2.0, 3.0], 1.0))

julia> isequivalent(Bproj, BallInf([1.0, 2], 1.0))
true
```
