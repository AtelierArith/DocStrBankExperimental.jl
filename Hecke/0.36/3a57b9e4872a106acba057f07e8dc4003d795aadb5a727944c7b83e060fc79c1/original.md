```
rref(M::SMat{T}; truncate = false) where {T <: FieldElement} -> (Int, SMat{T})
```

Return a tuple $(r, A)$ consisting of the rank $r$ of $M$ and a reduced row echelon form $A$ of $M$. If the function is called with `truncate = true`, the result will not contain zero rows, so `nrows(A) == rank(M)`.
