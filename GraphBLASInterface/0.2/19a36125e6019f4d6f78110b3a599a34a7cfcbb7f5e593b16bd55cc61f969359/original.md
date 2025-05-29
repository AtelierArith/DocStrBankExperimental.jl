```
GrB_eWiseAdd(C, mask, accum, op, A, B, desc)
```

Generic method for element-wise matrix and vector operations: using set union.

`GrB_eWiseAdd` computes `C<Mask> = accum (C, A + B)`, where pairs of elements in two matrices (or two vectors) are pairwise "added". The "add" operator can be any binary operator. With the plus operator, this is the same matrix addition in conventional linear algebra. The pattern of the result T = A + B is the set union of A and B. Entries outside of the union are not computed. That is, if both A(i, j) and B(i, j) are present in the pattern of A and B, then T(i, j) = A(i, j) "+" B(i, j). If only A(i, j) is present then T(i, j) = A (i, j) and the "+" operator is not used. Likewise, if only B(i, j) is in the pattern of B but A(i, j) is not in the pattern of A, then T(i, j) = B(i, j). For a semiring, the mult operator is the semiring's add operator.
