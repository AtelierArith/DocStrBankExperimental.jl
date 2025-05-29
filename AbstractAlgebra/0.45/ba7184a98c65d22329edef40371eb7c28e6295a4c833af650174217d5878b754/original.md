```
base_ring(a)
```

Return base ring $R$ of given element or parent $a$.

# Examples

```jldoctest
julia> S, x = polynomial_ring(QQ, :x)
(Univariate polynomial ring in x over rationals, x)

julia> base_ring(S) == QQ
true

julia> R = GF(7)
Finite field F_7

julia> base_ring(R)
Union{}
```
