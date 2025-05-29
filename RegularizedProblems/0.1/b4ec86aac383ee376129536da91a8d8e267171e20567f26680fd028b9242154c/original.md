```
model, nls_model, sol = group_lasso_model(; kwargs...)
```

Return an instance of an `NLPModel` and `NLSModel` representing the group-lasso problem, i.e., the under-determined linear least-squares objective

½ ‖Ax - b‖₂²,

where A has orthonormal rows and b = A * x̄ + ϵ, x̄ is sparse and ϵ is a noise vector following a normal distribution with mean zero and standard deviation σ. Note that with this format, all groups have a the same number of elements and the number of groups divides evenly into the total number of elements.

## Keyword Arguments

  * `m :: Int`: the number of rows of A (default: 200)
  * `n :: Int`: the number of columns of A, with `n` ≥ `m` (default: 512)
  * `g :: Int`: the number of groups (default: 16)
  * `ag :: Int`: the number of active groups (default: 5)
  * `noise :: Float64`: noise amount (default: 0.01)
  * `compound :: Int`: multiplier for `m`, `n`, `g`, and `ag` (default: 1).

## Return Value

An instance of a `FirstOrderModel` that represents the group-lasso problem. An instance of a `FirstOrderNLSModel` that represents the group-lasso problem. Also returns true x, number of groups g, group-index denoting which groups are active, and a Matrix where rows are group indices of x.
