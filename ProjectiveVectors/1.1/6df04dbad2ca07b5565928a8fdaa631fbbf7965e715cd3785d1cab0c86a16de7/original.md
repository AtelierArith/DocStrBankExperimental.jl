```
PVector{T, N} <: AbstractProjectiveVector{T, N}
```

A `PVector` represents a projective vector `z` which lives in a product of `N` projective spaces $P(T)^{dᵢ}$. The underlying data structure is a `Vector{T}`.

```
PVector(v::AbstractVector, dims::NTuple{N,Int}) where N
```

Create a projective vector `v` living in a product of projective spaces with (projective) dimensions `dims`.

```
PVector(v, w, ...)
```

Create the product of projective vectors.

## Example

```julia
julia> PVector([1,2,3], [4, 5])
[1 : 2 : 3] × [4 : 5]

julia> PVector([1, 2, 3, 4, 5], (2, 1))
[1 : 2 : 3] × [4 : 5]

julia> PVector([1,2,3], [4, 5], [6, 7, 8])
[1 : 2 : 3] × [4 : 5] × [6 : 7 : 8]
```
