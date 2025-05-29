```
m, factors = xdiv!(f, G)
```

多変数の多項式 `f` を多項式のベクトル `G` でインプレースに減少させます。定義によれば、`rem!` を適用した後、`G` の多項式の先頭項が `f` の任意の単項式を割り切らないことを意味し、`f + factors * G` は元の `f` の値の `m` 倍に等しくなります。

`xdiv!` と `div` の違いは、前者が分母を消去することを許可する点です。例えば、基底環が ℤ であっても `2x^2` を `3x` で減少させることができます。

# 例

1変数の場合、これは通常のユークリッドアルゴリズムに過ぎません：

```jldoctest
julia> using PolynomialRings

julia> R,(x,y) = polynomial_ring(:x, :y, basering=Complex{Int});

julia> f = x^2 + y^2 + 1
x^2 + y^2 + 1 + 0im

julia> xdiv!(f, [x-im])
(1 + 0im, @ring(Complex{Int64}[x,y])[x + 0 + 1im])

julia> f
y^2

julia> g = x^2 + y^2 + 1
x^2 + y^2 + 1 + 0im

julia> xdiv!(g, [x, y])
(1 + 0im, @ring(Complex{Int64}[x,y])[x y])

julia> g
1 + 0im
```
