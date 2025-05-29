```
multiplication_table(A::GroupAlgebra; copy::Bool = true) -> Matrix{RingElem}
```

群代数 $A$ が与えられたとき、この関数は $A$ の乗法表を返します：もし関数が $M$ を返し、$A$ の基底が $g_1,\dots, g_n$ であるなら、$g_i \cdot g_j = g_{M[i, j]}$ が成り立ちます。
