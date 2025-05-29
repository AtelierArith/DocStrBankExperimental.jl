```
implicit(solve, residual, x, p=(); drdy=drdy_forward, lsolve=linear_solve)
```

Make implicit function AD compatible (specifically with ForwardDiff and ReverseDiff).

# Arguments

  * `solve::function`: y = solve(x, p). Solve implicit function returning state variable y, for input variables x, and fixed parameters p.
  * `residual::function`: Either r = residual(y, x, p) or in-place residual!(r, y, x, p). Set residual r (scalar or vector), given state y (scalar or vector), variables x (vector) and fixed parameters p (tuple).
  * `x::vector{float}`: evaluation point.
  * `p::tuple`: fixed parameters. default is empty tuple.
  * `drdy::function`: drdy(residual, y, x, p).  Provide (or compute yourself): ∂r*i/∂y*j.  Default is forward mode AD.
  * `lsolve::function`: lsolve(A, b).  Linear solve A x = b  (where A is computed in drdy and b is computed in jvp, or it solves A^T x = c where c is computed in vjp).  Default is backslash operator.
