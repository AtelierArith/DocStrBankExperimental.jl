```
vcat(A::MatrixElem{T}...) where T <: NCRingElement -> MatrixElem
```

行列 $A$ の水平方向の連結を返します。すべての構成行列は同じ基底環と列数を持っている必要があります。
