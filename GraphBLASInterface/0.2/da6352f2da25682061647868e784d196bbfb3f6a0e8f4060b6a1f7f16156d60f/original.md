```
GrB_eWiseMult(C, mask, accum, op, A, B, desc)
```

Generic method for element-wise matrix and vector operations: using set intersection.

`GrB_eWiseMult` computes `C<Mask> = accum (C, A .* B)`, where pairs of elements in two matrices (or vectors) are pairwise "multiplied" with C(i, j) = mult (A(i, j), B(i, j)). The "multiplication" operator can be any binary operator. The pattern of the result T = A .* B is the set intersection (not union) of A and B. Entries outside of the intersection are not computed. This is primary difference with `GrB_eWiseAdd`. The input matrices A and/or B may be transposed first, via the descriptor. For a semiring, the mult operator is the semiring's multiply operator; this differs from the eWiseAdd methods which use the semiring's add operator instead.
