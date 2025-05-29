```
FISTA(A; AHA=A'*A, reg=L1Regularization(zero(real(eltype(AHA)))), normalizeReg=NoNormalization(), iterations=50, verbose = false, rho = 0.95 / power_iterations(AHA), theta=1, relTol=eps(real(eltype(AHA))), restart = :none)
FISTA( ; AHA=,     reg=L1Regularization(zero(real(eltype(AHA)))), normalizeReg=NoNormalization(), iterations=50, verbose = false, rho = 0.95 / power_iterations(AHA), theta=1, relTol=eps(real(eltype(AHA))), restart = :none)
```

creates a `FISTA` object for the forward operator `A` or normal operator `AHA`.

# Required Arguments

  * `A`                                                 - forward operator

OR

  * `AHA`                                               - normal operator (as a keyword argument)

# Optional Keyword Arguments

  * `AHA`                                               - normal operator is optional if `A` is supplied
  * `precon`                                            - preconditionner for the internal CG algorithm
  * `reg::AbstractParameterizedRegularization`          - regularization term; can also be a vector of regularization terms
  * `normalizeReg::AbstractRegularizationNormalization` - regularization normalization scheme; options are `NoNormalization()`, `MeasurementBasedNormalization()`, `SystemMatrixBasedNormalization()`
  * `rho::Real`                                         - step size for gradient step; the default is `0.95 / max_eigenvalue` as determined with power iterations.
  * `theta::Real`                                       - parameter for predictor-corrector step
  * `relTol::Real`                                      - tolerance for stopping criterion
  * `iterations::Int`                                   - maximum number of iterations
  * `restart::Symbol`                                   - `:none`, `:gradient` options for restarting
  * `verbose::Bool`                                     - print residual in each iteration

See also [`createLinearSolver`](@ref), [`solve!`](@ref).
