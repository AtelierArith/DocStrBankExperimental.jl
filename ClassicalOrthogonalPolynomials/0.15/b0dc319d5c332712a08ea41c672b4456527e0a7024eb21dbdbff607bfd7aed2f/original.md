```
JacobiWeight{T}(a,b)
JacobiWeight(a,b)
```

The quasi-vector representing the Jacobi weight function $(1-x)^a (1+x)^b$ on $[-1,1]$. See also [`jacobiweight`](@ref) and [`Jacobi`](@ref).

# Examples

```jldoctest
julia> J=JacobiWeight(1.0,1.0)
(1-x)^1.0 * (1+x)^1.0 on -1..1

julia> J[0.5]
0.75

julia> axes(J)
(Inclusion(-1.0 .. 1.0 (Chebyshev)),)
```
