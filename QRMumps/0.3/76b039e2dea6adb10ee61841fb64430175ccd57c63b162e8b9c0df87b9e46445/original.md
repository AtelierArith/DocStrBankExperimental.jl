```
qrm_update!(spmat, A)
qrm_update!(spmat, vals)
```

This routine updates a **qrm_spmat** type data structure from a **sparseMatrixCSC**. `spmat` and `A` must have the same sparsity pattern.

#### Input Arguments :

In the first form,

  * `spmat`: the **qrm_spmat** sparse matrix to be updated.
  * `A` : a Julia sparse matrix stored in **SparseMatrixCSC** format.

In the second form,

  * `vals`: the array of values of nonzero elements of `A`.
