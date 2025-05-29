```
cg!(x, A, b; kwargs...) -> x, [history]
```

# Arguments

  * `x`: Initial guess, will be updated in-place;
  * `A`: linear operator;
  * `b`: right-hand side.

## Keywords

  * `statevars::CGStateVariables`: Has 3 arrays similar to `x` to hold intermediate results;
  * `initially_zero::Bool`: If `true` assumes that `iszero(x)` so that one matrix-vector product can be saved when computing the initial residual vector;
  * `Pl = Identity()`: left preconditioner of the method. Should be symmetric, positive-definite like `A`;
  * `abstol::Real = zero(real(eltype(b)))`, `reltol::Real = sqrt(eps(real(eltype(b))))`: absolute and relative tolerance for the stopping condition `|r_k| ≤ max(reltol * |r_0|, abstol)`, where `r_k ≈ A * x_k - b` is approximately the residual in the `k`th iteration.

    !!! note
        The true residual norm is never explicitly computed during the iterations for performance reasons; it may accumulate rounding errors.
  * `maxiter::Int = size(A,2)`: maximum number of iterations;
  * `verbose::Bool = false`: print method information;
  * `log::Bool = false`: keep track of the residual norm in each iteration.

# Output

**if `log` is `false`**

  * `x`: approximated solution.

**if `log` is `true`**

  * `x`: approximated solution.
  * `ch`: convergence history.

**ConvergenceHistory keys**

  * `:tol` => `::Real`: stopping tolerance.
  * `:resnom` => `::Vector`: residual norm at each iteration.
