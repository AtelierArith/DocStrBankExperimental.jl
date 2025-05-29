```
idrs!(x, A, b; s = 8, kwargs...) -> x, [history]
```

Solve the problem $Ax = b$ approximately with IDR(s), where `s` is the dimension of the shadow space.

# Arguments

  * `x`: Initial guess, will be updated in-place;
  * `A`: linear operator;
  * `b`: right-hand side.

## Keywords

  * `s::Integer = 8`: dimension of the shadow space;
  * `Pl::precT`: left preconditioner,
  * `abstol::Real = zero(real(eltype(b)))`, `reltol::Real = sqrt(eps(real(eltype(b))))`: absolute and relative tolerance for the stopping condition `|r_k| ≤ max(reltol * |r_0|, abstol)`, where `r_k = A * x_k - b` is the residual in the `k`th iteration;
  * `maxiter::Int = size(A, 2)`: maximum number of iterations;
  * `log::Bool`: keep track of the residual norm in each iteration;
  * `verbose::Bool`: print convergence information during the iterations.

# Return values

**if `log` is `false`**

  * `x`: approximate solution.

**if `log` is `true`**

  * `x`: approximate solution;
  * `history`: convergence history.
