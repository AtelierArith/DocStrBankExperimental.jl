```
qrm_spmat_init!(spmat, A; sym=false)
spmat = qrm_spmat_init!(spmat, m, n, rows, cols, vals; sym=false)
```

This routine initializes a **qrm_spmat** type data structure from a **sparseMatrixCSC**.

#### Input Arguments :

In the first form,

  * `spmat`: the **qrm_spmat** sparse matrix to be initialized.
  * `A` : a Julia sparse matrix stored in either **SparseMatrixCSC** or **SparseMatrixCOO** format (see SparseMatricesCOO.jl for the second case).
  * `sym` : a boolean to specify if the matrix is symmetric / hermitian (true) or unsymmetric (false).

In the second form, the matrix `A` is specified using

  * `m`: the number of rows.
  * `n`: the number of columns.
  * `rows`: the array of row indices of nonzero elements.
  * `cols`: the array of column indices of nonzero elements.
  * `vals`: the array of values of nonzero elements.
