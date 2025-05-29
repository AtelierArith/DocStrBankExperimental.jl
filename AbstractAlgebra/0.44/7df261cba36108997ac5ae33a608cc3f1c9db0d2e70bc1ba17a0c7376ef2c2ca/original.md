```
polynomial_ring(R::Ring, n::Int, s::Symbol=:x; cached=true, internal_ordering=:lex)
```

Same as [`polynomial_ring(::Ring, ["s$i" for i in 1:n])`](@ref polynomial_ring(::Ring, ::Vector{Symbol})).

# Example

```jldoctest
julia> S, x = polynomial_ring(ZZ, 3)
(Multivariate polynomial ring in 3 variables over integers, AbstractAlgebra.Generic.MPoly{BigInt}[x1, x2, x3])
```
