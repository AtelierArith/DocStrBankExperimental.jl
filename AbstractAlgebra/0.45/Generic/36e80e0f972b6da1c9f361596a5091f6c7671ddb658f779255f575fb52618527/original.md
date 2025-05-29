```
matrix_repr(xi::SkewDiagram)
```

Return a sparse representation of the diagram `xi`, i.e. a sparse array `A` where `A[i,j] == 1` if and only if `(i,j)` is in `xi.lam` but not in `xi.mu`.
