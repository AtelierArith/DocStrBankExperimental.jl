```
mju_boxQP(res, R, index, H, g, lower, upper)
```

minimize 0.5*x'*H*x + x'*g  s.t. lower <= x <= upper, return rank or -1 if failed   inputs:     n           - problem dimension     H           - SPD matrix                n*n     g           - bias vector               n     lower       - lower bounds              n     upper       - upper bounds              n     res         - solution warmstart        n   return value:     nfree <= n  - rank of unconstrained subspace, -1 if failure   outputs (required):     res         - solution                  n     R           - subspace Cholesky factor  nfree*nfree    allocated: n*(n+7)   outputs (optional):     index       - set of free dimensions    nfree          allocated: n   notes:     the initial value of res is used to warmstart the solver     R must have allocatd size n*(n+7), but only nfree*nfree values are used in output     index (if given) must have allocated size n, but only nfree values are used in output     only the lower triangles of H and R and are read from and written to, respectively     the convenience function mju_boxQPmalloc allocates the required data structures

# Arguments

  * **`res::Vector{Float64}`** -> A vector of variable size. `res` should be a vector, not a matrix.
  * **`R::Matrix{Float64}`** -> A matrix of variable size. size of `R` should be n*(n+7).
  * **`index::Vector{Int32}`** -> An **optional** vector of variable size. `index` should be a vector, not a matrix. size of `index` should equal n. Can set to `nothing` if not required.
  * **`H::Matrix{Float64}`** -> A matrix of variable size. `H` should be of shape (n, n). Constant.
  * **`g::Vector{Float64}`** -> A vector of variable size. `g` should be a vector, not a matrix. size of `g` should equal n. Constant.
  * **`lower::Vector{Float64}`** -> An **optional** vector of variable size. `lower` should be a vector, not a matrix. size of `lower` should equal n. Can set to `nothing` if not required. Constant.
  * **`upper::Vector{Float64}`** -> An **optional** vector of variable size. `upper` should be a vector, not a matrix. size of `upper` should equal n. Can set to `nothing` if not required. Constant.
