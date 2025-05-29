```
P = kp_block_jacobi(A)
```

Construct a block-Jacobi preconditioner to accelerate Krylov solvers on GPU architectures.

The preconditioner is compatible with sparse matrices in CSR or CSC format stored on NVIDIA, AMD, and Intel GPUs. It also works on CPU with the CSC format.

#### Input argument

  * `A`: The square sparse matrix on the CPU or GPU from which diagonal blocks are extracted.

#### Output argument

  * `P`: preconditioner of type `AbstractKrylovPreconditioner`.
