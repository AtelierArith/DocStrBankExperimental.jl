```
isone(a)
```

$ a $ が乗法単位元であれば true を返し、そうでなければ false を返します。

# 例

```jldoctest
julia> S = matrix_space(ZZ, 2, 2); T = matrix_space(ZZ, 2, 3); U = matrix_space(ZZ, 3, 2);

julia> isone(S([1 0; 0 1]))
true

julia> isone(T([1 0 0; 0 1 0]))
false

julia> isone(U([1 0; 0 1; 0 0]))
false

julia> T, x = puiseux_series_field(QQ, 10, :x)
(Puiseux series field in x over rationals, x + O(x^11))

julia> isone(x), isone(T(1))
(false, true)
```
