```
iszero(a)
```

Return true if $a$ is the additative identity, else return false.

# Examples

```jldoctest
julia> T, x = puiseux_series_field(QQ, 10, :x)
(Puiseux series field in x over rationals, x + O(x^11))

julia> a = T(0)
O(x^10)

julia> iszero(a)
true
```
