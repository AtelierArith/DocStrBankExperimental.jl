```
PostImputingMatrix(W::AbstractMatrix{T}, ψ=zeros(T, size(W, 1))) where T
```

Construct a [`PostImputingMatrix`](@ref) with multiplication parameters `W` and default parameters `ψ`.

# Examples

```jldoctest
julia> PostImputingMatrix([1 2; 3 4])
2×2 PostImputingMatrix{Int64, Matrix{Int64}, Vector{Int64}}:
W:
 1  2
 3  4

ψ:
 0
 0
```

See also: [`PreImputingMatrix`](@ref).
