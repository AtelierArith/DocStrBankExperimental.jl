```
polynomial_ring(R::Ring, n::Int, s::Symbol=:x; cached=true, internal_ordering=:lex)
```

`[`polynomial*ring(::Ring, ["s:i" for i in 1:n])`](@ref polynomial*ring(::Ring, ::Vector{Symbol}))` と同じです。

# 例

```jldoctest
julia> S, x = polynomial_ring(ZZ, 3)
(Multivariate polynomial ring in 3 variables over integers, AbstractAlgebra.Generic.MPoly{BigInt}[x1, x2, x3])
```
