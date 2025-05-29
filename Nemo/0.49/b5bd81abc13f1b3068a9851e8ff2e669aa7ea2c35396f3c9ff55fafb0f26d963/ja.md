```
defining_polynomial([R::FqPolyRing], K::FqField)
```

`K`の定義多項式を、`K`の基底体上の多項式として返します。

多項式環`R`が指定されている場合、その多項式は`R`の要素となります。

# 例

```jldoctest
julia> K, a = finite_field(9, "a");

julia> defining_polynomial(K)
x^2 + 2*x + 2

julia> Ky, y = K["y"];

julia> L, b = finite_field(y^3 + y^2 + y + 2, "b");

julia> defining_polynomial(L)
y^3 + y^2 + y + 2
```
