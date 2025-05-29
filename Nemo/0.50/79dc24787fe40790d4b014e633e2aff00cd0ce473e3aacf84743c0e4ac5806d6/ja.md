```
degree(K::FqField) -> Int
```

与えられた有限体の基底体に対する次数を返します。

# 例

```jldoctest
julia> K, a = finite_field(3, 2, "a");

julia> degree(K)
2

julia> Kx, x = K["x"];

julia> L, b = finite_field(x^3 + x^2 + x + 2, "b");

julia> degree(L)
3
```
