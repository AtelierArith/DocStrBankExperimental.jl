```
is_upper_triangular(A::MatrixElem)
```

$$
A
$$

が上三角行列である場合、すなわち主対角線の下にあるすべての要素がゼロである場合に`true`を返します。この定義は非正方行列にも適用されることに注意してください。

`LinearAlgebra.istriu`のエイリアスです。

# 例

```jldoctest
julia> is_upper_triangular(QQ[1 2 ; 0 4])
true

julia> is_upper_triangular(QQ[1 0 ; 3 4])
false

julia> is_upper_triangular(QQ[1 2 ;])
true

julia> is_upper_triangular(QQ[1 ; 2])
false
```
