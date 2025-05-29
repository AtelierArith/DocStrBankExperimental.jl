```
gmres!(x, A, b; kwargs...) -> x, [history]
```

Solves the problem $Ax = b$ with restarted GMRES.

# Arguments

  * `x`: Initial guess, will be updated in-place;
  * `A`: linear operator;
  * `b`: right-hand side.

## Keywords

  * `initially_zero::Bool`: If `true` assumes that `iszero(x)` so that one matrix-vector product can be saved when computing the initial residual vector;
  * `abstol::Real = zero(real(eltype(b)))`, `reltol::Real = sqrt(eps(real(eltype(b))))`: absolute and relative tolerance for the stopping condition `|r_k| ≤ max(reltol * |r_0|, abstol)`, where `r_k = A * x_k - b`
  * `restart::Int = min(20, size(A, 2))`: restarts GMRES after specified number of iterations;
  * `maxiter::Int = size(A, 2)`: maximum number of inner iterations of GMRES;
  * `Pl`: left preconditioner;
  * `Pr`: right preconditioner;
  * `log::Bool`: keep track of the residual norm in each iteration;
  * `verbose::Bool`: print convergence information during the iterations.
  * `orth_meth::OrthogonalizationMethod = ModifiedGramSchmidt()`: orthogonalization method (ModifiedGramSchmidt(), ClassicalGramSchmidt(), DGKS())

# Return values

**if `log` is `false`**

  * `x`: approximate solution.

**if `log` is `true`**

  * `x`: approximate solution;
  * `history`: convergence history.
