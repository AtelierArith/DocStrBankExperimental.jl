```
basis(L::SimpleNumField) -> Vector{NumFieldElem}
```

単純拡張 $L/K$ の標準基底を返します。すなわち、要素 $1,a,\dotsc,a^{d - 1}$ で、ここで $d$ は $K$ の次数、$a$ は原始元です。

# 例

```jldoctest
julia> Qx, x = QQ["x"];

julia> K, a = number_field(x^2 - 2, "a");

julia> basis(K)
2-element Vector{AbsSimpleNumFieldElem}:
 1
 a
```
