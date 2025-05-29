```
P = kp_ic0(A)
```

Construct an incomplete Cholesky preconditioner with zero fill-in – IC(0), to accelerate Krylov solvers on GPU architectures.

The preconditioner is compatible with sparse matrices in CSR or CSC format stored on NVIDIA and AMD GPUs.

#### Input argument

  * `A`: The sparse Hermitian and positive definite matrix on the GPU to factorize incompletely.

#### Output argument

  * `P`: preconditioner of type `AbstractKrylovPreconditioner`.
