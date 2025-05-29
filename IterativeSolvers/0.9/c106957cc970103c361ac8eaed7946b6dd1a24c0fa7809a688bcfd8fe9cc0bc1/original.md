```
qmr!(x, A, b; kwargs...) -> x, [history]
```

Solves the problem $Ax = b$ with the Quasi-Minimal Residual (QMR) method.

# Arguments

  * `x`: Initial guess, will be updated in-place;
  * `A`: linear operator;
  * `b`: right-hand side.

## Keywords

  * `initially_zero::Bool`: If `true` assumes that `iszero(x)` so that one matrix-vector product can be saved when computing the initial residual vector;
  * `maxiter::Int = size(A, 2)`: maximum number of iterations;
  * `abstol::Real = zero(real(eltype(b)))`, `reltol::Real = sqrt(eps(real(eltype(b))))`: absolute and relative tolerance for the stopping condition `|r_k| ≤ max(reltol * |r_0|, abstol)`, where `r_k = A * x_k - b`
  * `log::Bool`: keep track of the residual norm in each iteration;
  * `verbose::Bool`: print convergence information during the iteration.

# Return values

**if `log` is `false`**

  * `x`: approximate solution.

**if `log` is `true`**

  * `x`: approximate solution;
  * `history`: convergence history.

[^Saad2003]: Saad, Y. (2003). Interactive method for sparse linear system.

[^Freund1990]: Freund, W. R., & Nachtigal, N. M. (1990). QMR : for a Quasi-Minimal Residual Linear Method Systems. (December).
