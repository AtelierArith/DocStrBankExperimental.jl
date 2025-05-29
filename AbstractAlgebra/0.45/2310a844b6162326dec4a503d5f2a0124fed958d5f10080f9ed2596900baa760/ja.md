```
is_diagonal(A::MatrixElem)
```

$$
A
$$

が対角行列である場合、すなわち主対角線以外のすべてのエントリがゼロである場合に`true`を返します。この定義は、非正方行列にも適用されることに注意してください。

`LinearAlgebra.isdiag`のエイリアスです。

# 例

```jldoctest
julia> is_diagonal(QQ[1 0 ; 0 4])
true

julia> is_diagonal(QQ[1 2 ; 3 4])
false

julia> is_diagonal(QQ[1 0 ;])
true
```
