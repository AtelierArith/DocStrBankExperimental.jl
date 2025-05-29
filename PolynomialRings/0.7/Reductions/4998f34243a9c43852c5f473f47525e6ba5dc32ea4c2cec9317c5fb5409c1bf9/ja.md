```
any_reductions = xrem!(f, G)
```

多変数の多項式 `f` を多項式のベクトル `G` でインプレースに削減します。定義によれば、`rem!` を適用した後、`G` の多項式の先頭項が `f` の任意の単項式を割り切らないことを意味します。また、`f + factors * G` は、スカラー `m` と行ベクトル `factors` に対して、元の `f` の値の `m` 倍に等しくなります。

戻り値 `any_reductions` は、`factors` がゼロでない場合にのみ `true` になります。なお、`factors` 自体は実際には計算されず、返されません。これを取得する必要がある場合は、`xdiv!` を使用してください。`m` についても同様です。

`xdiv!` と `div` の違いは、前者が分母を消去することを許可する点です。例えば、基底環が ℤ であっても `2x^2` を `3x` で削減できます。

# 例

1 変数の場合、これは通常のユークリッドアルゴリズムです：

```jldoctest
julia> using PolynomialRings

julia> R,(x,y) = polynomial_ring(:x, :y, basering=Complex{Int});

julia> f = x^2 + 1
x^2 + 1 + 0im

julia> xrem!(f, [x-im])
true

julia> f
0

julia> g = x^2 + y^2 + 1
x^2 + y^2 + 1 + 0im

julia> xrem!(g, [x, y])
true

julia> g
1 + 0im
```
