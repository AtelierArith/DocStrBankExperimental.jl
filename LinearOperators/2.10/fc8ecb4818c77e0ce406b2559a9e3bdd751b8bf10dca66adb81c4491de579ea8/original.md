```
opLDL(M, [check=false])
```

Inverse of a symmetric matrix as a linear operator using its LDLᵀ factorization if it exists. The factorization is computed only once. The optional `check` argument will perform a cheap hermicity check.

If M is sparse and real, then only the upper triangle should be stored in order to use  [`LDLFactorizations.jl`](https://github.com/JuliaSmoothOptimizers/LDLFactorizations.jl):

```
using LDLFactorizations
triu!(M)
opLDL(Symmetric(M, :U))
```
