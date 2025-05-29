```
universal_polynomial_ring(R::Ring, varnames::Vector{Symbol}; cached::Bool=true, internal_ordering::Symbol=:lex)
universal_polynomial_ring(R::Ring; cached::Bool=true, internal_ordering::Symbol=:lex)
```

Given a coefficient ring `R` and variable names, say `varnames = [:x1, :x2, ...]`, return a tuple `S, [x1, x2, ...]` of the universal polynomial ring `S = R[x1, x2, \dots]` and its generators `x1, x2, \dots`.

If `varnames` is omitted, return an object representing the universal polynomial ring `S = R[\ldots]` with no variables in it initially.

# Examples

```jldoctest
julia> S, (x,y) = universal_polynomial_ring(ZZ, [:x,:y])
(Universal Polynomial Ring over Integers, AbstractAlgebra.Generic.UnivPoly{BigInt}[x, y])

julia> z = gen(S, :z)
z

julia> x*y - z
x*y - z

julia> S = universal_polynomial_ring(ZZ)
Universal Polynomial Ring over Integers

julia> x = gen(S, :x)
x

julia> y, z = gens(S, [:y, :z])
(y, z)

julia> x*y - z
x*y - z
```
