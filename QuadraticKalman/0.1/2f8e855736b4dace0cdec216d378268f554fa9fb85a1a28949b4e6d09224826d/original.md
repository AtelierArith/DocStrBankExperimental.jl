```
model_to_params(model::QKModel{T, T2}) where {T<:Real, T2}
```

Convert a QKModel object into a vector of unconstrained parameters.

The ordering of the parameters is as follows:

1. **State parameters:**

      * `mu` (length N)
      * `Phi` (N×N, stored columnwise)
      * Unconstrained parameters for the state noise scaling factor Ω: For each row `i = 1,...,N` and column `j = 1,...,i` (i.e. the lower–triangular part):

          * If `i == j`: the parameter is `log(Ω[i,i])`
          * Else: the parameter is `Ω[i,j]`
2. **Measurement parameters:**

      * `A` (length M)
      * `B` (M×N, stored columnwise)
      * `C` (a vector of M matrices; each matrix is N×N and is flattened columnwise)
      * Unconstrained parameters for the measurement noise scaling factor D: For each row `i = 1,...,M` and column `j = 1,...,i`:

          * If `i == j`: the parameter is `log(D[i,i])`
          * Else: the parameter is `D[i,j]`
      * `alpha` (M×M, stored columnwise)

# Returns

A vector of unconstrained parameters that, when passed to `params_to_model`, reconstructs the original QKModel.
