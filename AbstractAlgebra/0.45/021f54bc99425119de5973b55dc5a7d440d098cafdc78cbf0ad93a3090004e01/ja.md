```
iszero(a)
```

$$
a
$$

が加法的単位元であればtrueを返し、そうでなければfalseを返します。

# 例

```jldoctest
julia> T, x = puiseux_series_field(QQ, 10, :x)
(Puiseux series field in x over rationals, x + O(x^11))

julia> a = T(0)
O(x^10)

julia> iszero(a)
true
```
