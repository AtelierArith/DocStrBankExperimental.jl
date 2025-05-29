`GenericFactorization(;fact_alg=LinearAlgebra.factorize)`: Constructs a linear solver from a generic factorization algorithm `fact_alg` which complies with the Base.LinearAlgebra factorization API. Quoting from Base:

```
  * If `A` is upper or lower triangular (or diagonal), no factorization of `A` is
    required. The system is then solved with either forward or backward substitution.
    For non-triangular square matrices, an LU factorization is used.
    For rectangular `A` the result is the minimum-norm least squares solution computed by a
    pivoted QR factorization of `A` and a rank estimate of `A` based on the R factor.
    When `A` is sparse, a similar polyalgorithm is used. For indefinite matrices, the `LDLt`
    factorization does not use pivoting during the numerical factorization and therefore the
    procedure can fail even for invertible matrices.
```

## Keyword Arguments

  * fact_alg: the factorization algorithm to use. Defaults to `LinearAlgebra.factorize`, but can be swapped to choices like `lu`, `qr`
