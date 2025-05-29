```
is_unit(a::T) where {T <: NCRingElement}
```

$ a $ が可逆であれば true を返し、そうでなければ false を返します。

# 例

```jldoctest
julia> S, x = polynomial_ring(QQ, :x)
(Univariate polynomial ring in x over rationals, x)

julia> is_unit(x), is_unit(S(1)), is_unit(S(4))
(false, true, true)

julia> is_unit(ZZ(-1)), is_unit(ZZ(4))
(true, false)
```
