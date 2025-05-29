```
PostImputingMatrix{T <: Number, U <: AbstractMatrix{T}, V <: AbstractVector{T}} <: AbstractMatrix{T}
```

A parametrized matrix that fills in a default vector of parameters whenever a "missing" column is encountered during multiplication.

Supports multiplication with [`NGramMatrix`](@ref), [`MaybeHotMatrix`](@ref) and [`MaybeHotVector`](@ref). For any other `AbstractMatrix` it falls back to standard multiplication.

# Examples

```jldoctest
julia> A = PostImputingMatrix(ones(2, 2), -ones(2))
2×2 PostImputingMatrix{Float64, Matrix{Float64}, Vector{Float64}}:
W:
 1.0  1.0
 1.0  1.0

ψ:
 -1.0
 -1.0

julia> A * maybehotbatch([1, missing], 1:2)
2×2 Matrix{Float64}:
 1.0  -1.0
 1.0  -1.0
```

See also: [`PreImputingMatrix`](@ref).
