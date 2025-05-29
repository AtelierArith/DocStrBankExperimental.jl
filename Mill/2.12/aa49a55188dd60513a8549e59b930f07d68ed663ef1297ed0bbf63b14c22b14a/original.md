```
postimputing_dense(d_in, d_out, σ)
```

Like `Flux.Dense`, but use a [`PostImputingMatrix`](@ref) instead of a standard matrix.

# Examples

```jldoctest
julia> d = postimputing_dense(3, 2)
[postimputing]Dense(3 => 2)  3 arrays, 10 params, 168 bytes

julia> typeof(d.weight)
PostImputingMatrix{Float32, Matrix{Float32}, Vector{Float32}}

julia> typeof(d.bias)
Vector{Float32} (alias for Array{Float32, 1})
```

See also: [`PostImputingMatrix`](@ref), [`preimputing_dense`](@ref), [`PreImputingMatrix`](@ref).
