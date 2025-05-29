```
base_ring(a)
```

与えられた要素または親 $a$ の基底環 $R$ を返します。

# 例

```jldoctest
julia> S, x = polynomial_ring(QQ, :x)
(Univariate polynomial ring in x over rationals, x)

julia> base_ring(S) == QQ
true

julia> R = GF(7)
有限体 F_7

julia> base_ring(R)
Union{}
```
