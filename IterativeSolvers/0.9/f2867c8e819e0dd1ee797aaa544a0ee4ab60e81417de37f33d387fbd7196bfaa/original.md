```
lsqr!(x, A, b; kwargs...) -> x, [history]
```

Minimizes $\|Ax - b\|^2 + \|damp*x\|^2$ in the Euclidean norm. If multiple solutions exists returns the minimal norm solution.

The method is based on the Golub-Kahan bidiagonalization process. It is algebraically equivalent to applying CG to the normal equations $(A^*A + λ^2I)x = A^*b$ but has better numerical properties, especially if A is ill-conditioned.

# Arguments

  * `x`: Initial guess, will be updated in-place;
  * `A`: linear operator;
  * `b`: right-hand side.

## Keywords

  * `damp::Number = 0`: damping parameter.
  * `atol::Number = 1e-6`, `btol::Number = 1e-6`: stopping tolerances. If both are 1.0e-9 (say), the final residual norm should be accurate to about 9 digits. (The final `x` will usually have fewer correct digits, depending on `cond(A)` and the size of damp).
  * `conlim::Number = 1e8`: stopping tolerance.  `lsmr` terminates if an estimate of `cond(A)` exceeds conlim.  For compatible systems Ax = b, conlim could be as large as 1.0e+12 (say).  For least-squares problems, conlim should be less than 1.0e+8. Maximum precision can be obtained by setting `atol` = `btol` = `conlim` = zero, but the number of iterations may then be excessive.
  * `maxiter::Int = maximum(size(A))`: maximum number of iterations.
  * `verbose::Bool = false`: print method information.
  * `log::Bool = false`: output an extra element of type `ConvergenceHistory` containing extra information of the method execution.

# Return values

**if `log` is `false`**

  * `x`: approximated solution.

**if `log` is `true`**

  * `x`: approximated solution.
  * `ch`: convergence history.

**ConvergenceHistory keys**

  * `:atol` => `::Real`: atol stopping tolerance.
  * `:btol` => `::Real`: btol stopping tolerance.
  * `:ctol` => `::Real`: ctol stopping tolerance.
  * `:anorm` => `::Real`: anorm.
  * `:rnorm` => `::Real`: rnorm.
  * `:cnorm` => `::Real`: cnorm.
  * `:resnom` => `::Vector`: residual norm at each iteration.
