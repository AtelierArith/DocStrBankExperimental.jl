```
is_unit(a::T) where {T <: NCRingElement}
```

Return true if $a$ is invertible, else return false.

# Examples

```jldoctest
julia> S, x = polynomial_ring(QQ, :x)
(Univariate polynomial ring in x over rationals, x)

julia> is_unit(x), is_unit(S(1)), is_unit(S(4))
(false, true, true)

julia> is_unit(ZZ(-1)), is_unit(ZZ(4))
(true, false)
```
