```
polynomial_ring(R::NCRing, s::VarName = :x; cached::Bool = true)
```

Given a base ring `R` and symbol/string `s` specifying how the generator (variable) should be printed, return a tuple `S, x` representing the new polynomial ring $S = R[x]$ and the generator $x$ of the ring.

By default the parent object `S` depends only on `R` and `x` and will be cached. Setting the optional argument `cached` to `false` will prevent the parent object `S` from being cached.

# Examples

```jldoctest
julia> R, x = polynomial_ring(ZZ, :x)
(Univariate polynomial ring in x over integers, x)

julia> S, y = polynomial_ring(R, :y)
(Univariate polynomial ring in y over R, y)
```
