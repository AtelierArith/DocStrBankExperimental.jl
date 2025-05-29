```
number_field(f::Vector{PolyRingElem{<:NumFieldElem}}, s::VarName="_\$", check = true)
                                          -> NumField, Vector{NumFieldElem}
```

与えられたリスト $f_1, \ldots, f_n$ の単変数多項式が $K[x]$ の中で、ある数体 $K$ の上にある場合、拡張 $K[x_1, \ldots, x_n]/(f_1(x_1), \ldots, f_n(x_n))$ を構築します。

# 例

```jldoctest
julia> Qx, x = QQ["x"];

julia> K, a = number_field([x^2 - 2, x^2 - 3], "a")
(非単純数体、QQの上での次数4, AbsNonSimpleNumFieldElem[a1, a2])
```
