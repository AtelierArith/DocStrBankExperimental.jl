```
coeff(a::MPolyRingElem{T}, vars::Vector{Int}, exps::Vector{Int}) where T <: RingElement
```

与えられたインデックスの変数の積を、与えられた指数に上げた単項式からなる $a$ の「係数」を返します（すべての変数が現れる必要はなく、指数はゼロであってもかまいません）。例えば、`coeff(f, [1, 3], [0, 2])` は、$f$ の多項式における $x^0*z^2$ の係数を返します（変数がその順序で $x, y, z$ であると仮定します）。
