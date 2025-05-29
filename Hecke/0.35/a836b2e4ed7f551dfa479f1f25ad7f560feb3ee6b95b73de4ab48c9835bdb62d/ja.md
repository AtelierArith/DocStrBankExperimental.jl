```
trace_matrix(A::AbstractAssociativeAlgebra) -> MatElem
```

行列 $M$ を返します。これは $A$ の基底環上の行列であり、$M_{i, j} = \mathrm{tr}(b_i \cdot b_j)$ となります。ここで、$b_1, \dots, b_n$ は $A$ の基底です。
