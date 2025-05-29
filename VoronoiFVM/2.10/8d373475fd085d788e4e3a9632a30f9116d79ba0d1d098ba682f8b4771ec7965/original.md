```julia
inplace_linsolve!(A, b, ipiv)

```

Non-allocating, pivoting, inplace solution of square linear system of equations `A*x=b` using LU factorization from RecursiveFactorizations.jl.  

After solution, `A` will contain the LU factorization, and `b` the result. `ipiv` must be an Int64 vector of the same length as `b`.
