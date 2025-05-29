```
base_ring_type(a)
```

与えられた要素、要素の型、親または親の型 $a$ の基底環の型を返します。

# 例

```jldoctest
julia> R, x = polynomial_ring(ZZ, :x)
(Univariate polynomial ring in x over integers, x)

julia> base_ring_type(R) == typeof(base_ring(R))
true

julia> base_ring_type(zero(R)) == typeof(base_ring(zero(R)))
true

julia> base_ring_type(typeof(R)) == typeof(base_ring(R))
true

julia> base_ring_type(typeof(zero(R))) == typeof(base_ring(zero(R)))
true
```
