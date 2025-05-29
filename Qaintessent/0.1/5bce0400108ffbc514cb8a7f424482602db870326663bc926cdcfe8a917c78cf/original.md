```
matrix(::AbstractGate)
```

returns dense matrix representation of [`AbstractGate`](@ref) objects

# Examples

```jldoctest
julia> matrix(X)
2×2 Array{Complex{Float64},2}:
 0.0+0.0im  1.0+0.0im
 1.0+0.0im  0.0+0.0im
```
