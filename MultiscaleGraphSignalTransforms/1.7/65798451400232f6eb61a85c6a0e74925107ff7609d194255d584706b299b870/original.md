```
function dmatrix_ldb_flatten(dmatrix::Array{Float64,3}...; dm::Symbol = :KLdivergence)
```

Flatten dmatrices using the LDB method; after this function is called, it returns a matrix of size (~, ~, 1).

### Input Arguments

  * `dmatrix::Array{Float64,3}`: the matrix of LDB expansion coefficients in one class.
  * `dm::Symbol`: discriminant measure. Options: `:KLdivergence` (default),   `:Jdivergence`, `:l1`, `:l2`, and `:Hellinger`.

### Example Usage:

`dmatrix_ldb_flatten(dmatrix1, dmatrix2, dmatrix3)`, each argument is the expansion coefficient matrix of a class of signals. It uses the default discriminant measure KL divergence to flatten these matrices. In other words, it flattens these expansion coefficent matrices by computing and summing "statistical distances" among them.
