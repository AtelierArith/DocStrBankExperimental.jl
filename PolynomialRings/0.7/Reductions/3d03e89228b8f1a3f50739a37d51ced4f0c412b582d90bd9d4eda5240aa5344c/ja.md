```
factors = div!(f, G)
```

多変数の多項式 `f` を多項式のベクトル `G` でインプレースに削減します。定義によれば、`rem!` を適用した後、`G` の多項式の先頭項が `f` の任意の単項式を割り切らないことを意味し、`f + factors * G` は元の `f` の値に等しくなります。

返り値は、削減が行われなかった場合は `nothing` です。この状況はゼロベクトルでも表現できますが、効率のために `nothing` を選択します。

分母をクリアすることを許可したい場合、例えば基底環が ℤ であっても `2x^2` を `3x` で削減するには、代わりに `xdiv!` を使用してください。

# 例

1変数の場合、これは通常のユークリッドアルゴリズムです：

```jldoctest
julia> using PolynomialRings

julia> R,(x,y) = polynomial_ring(:x, :y, basering=Complex{Int});

julia> f = x^2 + 1 + 0im
x^2 + 1 + 0im

julia> collect(div!(f, [x-im]))
1×1 Array{@ring(Complex{Int64}[x,y]),2}:
 x + 0 + 1im

julia> f
0

julia> g = x^2 + y^2 + 1
x^2 + y^2 + 1 + 0im

julia> collect(div!(g, [x, y]))
1×2 Array{@ring(Complex{Int64}[x,y]),2}:
 x  y

julia> g
1 + 0im
```
