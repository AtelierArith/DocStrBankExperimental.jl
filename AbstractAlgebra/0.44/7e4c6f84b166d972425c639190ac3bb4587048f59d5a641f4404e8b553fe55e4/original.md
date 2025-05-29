```
polynomial_ring(R::Ring, varnames::Vector{Symbol}; cached=true, internal_ordering=:lex)
```

Given a coefficient ring `R` and variable names, say `varnames = [:x1, :x2, ...]`, return a tuple `S, [x1, x2, ...]` of the polynomial ring $S = R[x1, x2, \dots]$ and its generators $x1, x2, \dots$.

By default (`cached=true`), the output `S` will be cached, i.e. if `polynomial_ring` is invoked again with the same arguments, the same (*identical*) ring is returned. Setting `cached` to `false` ensures a distinct new ring is returned, and will also prevent it from being cached.

The monomial ordering used for the internal storage of polynomials in `S` can be set with `internal_ordering` and must be one of `:lex`, `:deglex` or `:degrevlex`.

See also: [`polynomial_ring(::Ring, ::Vararg)`](@ref), [`@polynomial_ring`](@ref).

# Example

```jldoctest
julia> S, generators = polynomial_ring(ZZ, [:x, :y, :z])
(Multivariate polynomial ring in 3 variables over integers, AbstractAlgebra.Generic.MPoly{BigInt}[x, y, z])
```
