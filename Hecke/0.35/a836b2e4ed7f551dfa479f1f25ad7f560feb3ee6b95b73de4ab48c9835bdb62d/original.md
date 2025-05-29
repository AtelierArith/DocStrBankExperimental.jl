```
trace_matrix(A::AbstractAssociativeAlgebra) -> MatElem
```

Returns a matrix $M$ over the base ring of $A$ such that $M_{i, j} = \mathrm{tr}(b_i \cdot b_j)$, where $b_1, \dots, b_n$ is the basis of $A$.
