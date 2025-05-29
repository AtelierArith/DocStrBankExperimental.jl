```
zero(a)
```

代数構造 $a$ における加法単位元を返します。これは要素または親である可能性があります。

# 例

```jldoctest
julia> S = matrix_ring(QQ, 2)
Matrix ring of degree 2
  over rationals

julia> zero(S)
[0//1   0//1]
[0//1   0//1]

julia> R, x = polynomial_ring(ZZ, :x)
(Univariate polynomial ring in x over integers, x)

julia> zero(x^3 + 2)
0
```
