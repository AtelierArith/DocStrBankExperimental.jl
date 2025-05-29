```
is_lower_triangular(A::MatrixElem)
```

$$
A
$$

が下三角行列である場合は`true`を返します。つまり、主対角線の上にあるすべての要素がゼロである必要があります。この定義は、非正方行列にも適用されることに注意してください。

`LinearAlgebra.istril`のエイリアスです。

# 例

```jldoctest
julia> is_lower_triangular(QQ[1 2 ; 0 4])
false

julia> is_lower_triangular(QQ[1 0 ; 3 4])
true

julia> is_lower_triangular(QQ[1 2 ;])
false

julia> is_lower_triangular(QQ[1 ; 2])
true
```
