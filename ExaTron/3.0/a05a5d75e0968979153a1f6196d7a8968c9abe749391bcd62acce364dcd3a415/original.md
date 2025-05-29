Subroutine dicf

Given a sparse symmetric matrix A in compressed row storage, this subroutine computes an incomplete Cholesky factorization.

Implementation of dicf is based on the Jones-Plassmann code. Arrays indf and list define the data structure. At the beginning of the computation of the j-th column,

```
For k < j, indf[k] is the index of A for the first
nonzero l[i,k] in the k-th column with i >= j.

For k < j, list[i] is a pointer to a linked list of column
indices k with i = L.rowval[indf[k]].
```

For the computation of the j-th column, the array indr records the row indices. Hence, if nlj is the number of nonzeros in the j-th column, then indr[1],...,indr[nlj] are the row indices. Also, for i > j, indf[i] marks the row indices in the j-th column so that indf[i] = 1 if l[i,j] is not zero.

MINPACK-2 Project. May 1998. Argonne National Laboratory. Chih-Jen Lin and Jorge J. More'.
