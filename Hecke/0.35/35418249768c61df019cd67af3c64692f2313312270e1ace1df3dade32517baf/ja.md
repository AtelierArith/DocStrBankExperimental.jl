```
multiplication_table(A::MatAlgebra; copy::Bool = true) -> Array{RingElem, 3}
```

代数 $A$ が与えられたとき、この関数は $A$ の乗法表を返します：もし関数が $M$ を返し、$A$ の基底が $e_1,\dots, e_n$ であるなら、$e_i \cdot e_j = \sum_k M[i, j, k] \cdot e_k$ が成り立ちます。
