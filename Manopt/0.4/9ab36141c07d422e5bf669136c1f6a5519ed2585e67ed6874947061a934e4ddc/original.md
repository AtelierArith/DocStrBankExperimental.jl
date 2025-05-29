```
LanczosState{P,T,SC,B,I,R,TM,V,Y} <: AbstractManoptSolverState
```

Solve the adaptive regularized subproblem with a Lanczos iteration

# Fields

  * `stop`:            the stopping criterion
  * `σ`:               the current regularization parameter
  * `X`:               the Iterate
  * `Lanczos_vectors`: the obtained Lanczos vectors
  * `tridig_matrix`:   the tridiagonal coefficient matrix T
  * `coefficients`:    the coefficients $y_1,...y_k$ that determine the solution
  * `Hp`:              a temporary vector containing the evaluation of the Hessian
  * `Hp_residual`:     a temporary vector containing the residual to the Hessian
  * `S`:               the current obtained / approximated solution
