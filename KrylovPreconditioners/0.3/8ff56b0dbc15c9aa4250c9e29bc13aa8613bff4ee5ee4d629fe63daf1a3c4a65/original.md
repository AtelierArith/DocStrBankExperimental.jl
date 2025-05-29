```
KrylovOperator(A; nrhs::Int=1, transa::Char='N')
```

Create a Krylov operator to accelerate sparse matrix-vector or matrix-matrix products on GPU architectures. The operator is compatible with sparse matrices stored on NVIDIA, AMD, and Intel GPUs.

#### Input arguments

  * `A`: The sparse matrix on the GPU that serves as the operator for matrix-vector or matrix-matrix products;
  * `nrhs`: Specifies the number of columns for the right-hand sides. Defaults to `1` for standard matrix-vector products;
  * `transa`: Determines how the matrix `A` is applied during the products; `'N'` for no transposition, `'T'` for transpose, and `'C'` for conjugate transpose.

#### Output argument

  * `op`: An instance of `AbstractKrylovOperator` representing the Krylov operator for the specified sparse matrix and parameters.
