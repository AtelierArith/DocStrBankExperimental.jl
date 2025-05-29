```
cholesky(K::AbstractKroneckerProduct; check = true)
```

Wrapper around `cholesky` from the `LinearAlgebra` package. Performs Cholesky on the matrices of a `AbstractKroneckerProduct` instances and returns a `CholeskyKronecker` type. Similar to `Cholesky`, `size`, `\`, `inv`, `det`, and `logdet` are overloaded to efficiently work with this type.
