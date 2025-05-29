```
minres!(x, A, b; kwargs...) -> x, [history]
```

Solve Ax = b for (skew-)Hermitian matrices A using MINRES.

# Arguments

  * `x`: initial guess, will be updated in-place;
  * `A`: linear operator;
  * `b`: right-hand side.

## Keywords

  * `initially_zero::Bool = false`: if `true` assumes that `iszero(x)` so that one matrix-vector product can be saved when computing the initial residual vector;
  * `skew_hermitian::Bool = false`: if `true` assumes that `A` is skew-symmetric or skew-Hermitian;
  * `abstol::Real = zero(real(eltype(b)))`, `reltol::Real = sqrt(eps(real(eltype(b))))`: absolute and relative tolerance for the stopping condition `|r_k| ≤ max(reltol * |r_0|, abstol)`, where `r_k = A * x_k - b` is the residual in the `k`th iteration

    !!! note
        The residual is computed only approximately.
  * `maxiter::Int = size(A, 2)`: maximum number of iterations;
  * `log::Bool = false`: keep track of the residual norm in each iteration;
  * `verbose::Bool = false`: print convergence information during the iterations.

# Return values

**if `log` is `false`**

  * `x`: approximate solution.

**if `log` is `true`**

  * `x`: approximate solution;
  * `history`: convergence history.
