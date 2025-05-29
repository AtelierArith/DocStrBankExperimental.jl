```
preimputing_dense(in, out, σ)
```

Like `Flux.Dense`, but use a [`PreImputingMatrix`](@ref) instead of a standard matrix.

# Examples

```jldoctest
julia> d = preimputing_dense(2, 3)
[preimputing]Dense(2 => 3)  3 arrays, 11 params, 172 bytes

julia> typeof(d.weight)
PreImputingMatrix{Float32, Matrix{Float32}, Vector{Float32}}

julia> typeof(d.bias)
Vector{Float32} (alias for Array{Float32, 1})
```

See also: [`PreImputingMatrix`](@ref), [`postimputing_dense`](@ref), [`PostImputingMatrix`](@ref).
