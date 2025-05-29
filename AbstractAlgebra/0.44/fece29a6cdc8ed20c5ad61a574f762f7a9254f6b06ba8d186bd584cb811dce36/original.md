```
lu(A::MatrixElem{T}, P = SymmetricGroup(nrows(A))) where {T <: FieldElement}
```

Return a tuple $r, p, L, U$ consisting of the rank of $A$, a permutation $p$ of $A$ belonging to $P$, a lower triangular matrix $L$ and an upper triangular matrix $U$ such that $p(A) = LU$, where $p(A)$ stands for the matrix whose rows are the given permutation $p$ of the rows of $A$.
