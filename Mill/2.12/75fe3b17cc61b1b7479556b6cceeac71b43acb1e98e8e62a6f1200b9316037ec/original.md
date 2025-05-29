```
PreImputingMatrix(W::AbstractMatrix{T}, ψ=zeros(T, size(W, 2))) where T
```

Construct a [`PreImputingMatrix`](@ref) with multiplication parameters `W` and default parameters `ψ`.

# Examples

```jldoctest
julia> PreImputingMatrix([1 2; 3 4])
2×2 PreImputingMatrix{Int64, Matrix{Int64}, Vector{Int64}}:
W:
 1  2
 3  4

ψ:
 0  0
```

See also: [`PostImputingMatrix`](@ref).
