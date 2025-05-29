```
f_red = xrem(f, G)
```

多変数の多項式 `f` を多項式のベクトル `G` で減算します。定義により、これは `G` の多項式の先頭項が `f` の任意の単項式を割り切らないことを意味し、`f_red + factors * G == m * f` となるような因子と整数 `m` が存在します。

因子のベクトルを取得する必要がある場合は、代わりに `xdivrem` を使用してください。

# 例

1変数の場合、これは通常のユークリッドアルゴリズムです：

```jldoctest
julia> using PolynomialRings

julia> R,(x,y) = polynomial_ring(:x, :y, basering=Complex{Int});

julia> xrem(x^2 + 1, [x-im])
0

julia> xrem(x^2 + y^2 + 1, [x, y])
1 + 0im
```
