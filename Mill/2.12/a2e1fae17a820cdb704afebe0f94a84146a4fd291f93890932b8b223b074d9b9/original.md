```
PreImputingMatrix{T <: Number, U <: AbstractMatrix{T}, V <: AbstractVector{T}} <: AbstractMatrix{T}
```

A parametrized matrix that fills in elements from a default vector of parameters whenever a `missing` element is encountered during multiplication.

# Examples

```jldoctest
julia> A = PreImputingMatrix(ones(2, 2), -ones(2))
2×2 PreImputingMatrix{Float64, Matrix{Float64}, Vector{Float64}}:
W:
 1.0  1.0
 1.0  1.0

ψ:
 -1.0  -1.0

julia> A * [0 1; missing -1]
2×2 Matrix{Float64}:
 -1.0  0.0
 -1.0  0.0
```

See also: [`PreImputingMatrix`](@ref).
