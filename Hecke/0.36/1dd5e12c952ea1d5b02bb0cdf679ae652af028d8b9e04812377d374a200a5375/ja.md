```
basis(L::NonSimpleNumField) -> Vector{NumFieldElem}
```

非単純拡張 $L/K$ の標準基底を返します。もし $L = K(a_1,\dotsc,a_n)$ であり、各 $a_i$ の次数が $d_i$ であるならば、基底は $a_1^{i_1}\dotsm a_d^{i_d}$ となり、$1 \leq j \leq n$ に対して $0 \leq i_j \leq d_j - 1$ です。

# 例

```jldoctest
julia> Qx, x = QQ["x"];

julia> K, (a1, a2) = number_field([x^2 - 2, x^2 - 3], "a");

julia> basis(K)
4-element Vector{AbsNonSimpleNumFieldElem}:
 1
 a1
 a2
 a1*a2
```
