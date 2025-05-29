```
eigen(K::AbstractKroneckerProduct)
```

Wrapper around `eigen` from the `LinearAlgebra` package. If the matrices of an `AbstractKroneckerProduct` instance are square, performs Eigenvalue decompositon on them and returns an `Eigen` type. Otherwise, it collects the instance and runs eigen on the full matrix. The functions, `\`, `inv`, and `logdet` are overloaded to efficiently work with this type.
