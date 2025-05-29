```
any_reductions = rem!(f, G)
```

多変数多項式 `f` を多項式のベクトル `G` でインプレースに減算します。定義によれば、`rem!` を適用した後、`G` の多項式の先頭項は `f` の任意の単項式を割り切らず、`f + factors * G` はある行ベクトル `factors` に対して元の `f` の値と等しくなります。

返り値 `any_reductions` は、`factors` がゼロでない場合にのみ `true` になります。なお、`factors` 自体は実際には計算されず、返されません。これを取得する必要がある場合は、`div!` を使用してください。

分母をクリアすることを許可したい場合、例えば基底環が ℤ であっても `2x^2` を `3x` で減算する場合は、代わりに `xrem!` を使用してください。

# 例

1変数の場合、これは通常のユークリッドアルゴリズムです：

```jldoctest
julia> using PolynomialRings

julia> R,(x,y) = polynomial_ring(:x, :y, basering=Complex{Int});

julia> f = x^2 + 1
x^2 + 1 + 0im

julia> rem!(f, [x-im])
true

julia> f
0

julia> g = x^2 + y^2 + 1
x^2 + y^2 + 1 + 0im

julia> rem!(g, [x, y])
true

julia> g
1 + 0im
```
