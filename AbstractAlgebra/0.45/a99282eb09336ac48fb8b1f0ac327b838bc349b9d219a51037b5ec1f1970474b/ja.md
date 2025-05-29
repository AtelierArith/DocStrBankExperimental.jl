```
one(a)
```

代数構造 $a$ における乗法単位元を返します。これは要素または親である可能性があります。

# 例

```jldoctest
julia> S = matrix_space(ZZ, 2, 2)
行列空間 2 行 2 列
  整数上

julia> one(S)
[1   0]
[0   1]

julia> R, x = puiseux_series_field(QQ, 4, :x)
(有理数上の $x$ に関するプイセュ系列体, $x + O(x^5)$)

julia> one(x)
1 + O(x^4)

julia> G = GF(5)
有限体 $F_5$

julia> one(G)
1
```
