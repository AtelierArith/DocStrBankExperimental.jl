```
inner_solve(is::InnerSolver,T_arit,nep;kwargs...)
```

Solves the projected linear problem with solver specied with `is`. This is to be used as an inner solver in an inner-outer iteration. T specifies which method to use. The most common choice is [`DefaultInnerSolver`](@ref). The function returns `(λv,V)` where `λv` is an array of eigenvalues and `V` a matrix with corresponding vectors. The struct `T_arit` defines the arithmetics used in the outer iteration and should prefereably also be used in the inner iteration.

Different inner_solve methods take different kwargs. These are standardized kwargs:

  * `neigs`: Number of wanted eigenvalues (but less or more may be returned)
  * `σ`: target specifying where eigenvalues
  * `λv`, `V`: Vector/matrix of guesses to be used as starting values
  * `j`: the jth eigenvalue in a min-max characterization
  * `tol`: Termination tolarance for inner solver
  * `inner_logger`: Determines how the inner solves are logged. See [`Logger`](@ref) for further references
