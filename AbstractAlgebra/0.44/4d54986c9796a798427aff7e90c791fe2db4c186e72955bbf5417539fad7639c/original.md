```
polynomial_ring(R::Ring, varnames...; cached=true, internal_ordering=:lex)
polynomial_ring(R::Ring, varnames::Tuple; cached=true, internal_ordering=:lex)
```

Like [`polynomial_ring(::Ring, ::Vector{Symbol})`](@ref) with more ways to give `varnames` as specified in [`variable_names`](@ref).

Return a tuple `S, generators...` with `generators[i]` corresponding to `varnames[i]`.

!!! note
    In the first method, `varnames` must not be empty, and if it consists of only one name, the univariate [`polynomial_ring(R::NCRing, s::VarName)`](@ref) method is called instead.


# Examples

```jldoctest
julia> S, (a, b, c) = polynomial_ring(ZZ, [:a, :b, :c])
(Multivariate polynomial ring in 3 variables over integers, AbstractAlgebra.Generic.MPoly{BigInt}[a, b, c])

julia> S, x, y = polynomial_ring(ZZ, :x => (1:2, 1:2), :y => 1:3);

julia> S
Multivariate polynomial ring in 7 variables x[1, 1], x[2, 1], x[1, 2], x[2, 2], ..., y[3]
  over integers

julia> x
2×2 Matrix{AbstractAlgebra.Generic.MPoly{BigInt}}:
 x[1, 1]  x[1, 2]
 x[2, 1]  x[2, 2]

julia> y
3-element Vector{AbstractAlgebra.Generic.MPoly{BigInt}}:
 y[1]
 y[2]
 y[3]
```
