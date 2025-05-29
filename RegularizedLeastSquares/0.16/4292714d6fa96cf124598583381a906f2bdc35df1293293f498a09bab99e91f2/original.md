```
OptISTA(A; AHA=A'*A, reg=L1Regularization(zero(real(eltype(AHA)))), normalizeReg=NoNormalization(), iterations=50, verbose = false, rho=0.95 / power_iterations(AHA), theta=1, relTol=eps(real(eltype(AHA))))
OptISTA( ; AHA=,     reg=L1Regularization(zero(real(eltype(AHA)))), normalizeReg=NoNormalization(), iterations=50, verbose = false, rho=0.95 / power_iterations(AHA), theta=1, relTol=eps(real(eltype(AHA))))
```

creates a `OptISTA` object for the forward operator `A` or normal operator `AHA`. OptISTA has a 2x better worst-case bound than FISTA, but actual performance varies by application. It stores 2 extra intermediate variables the size of the image compared to FISTA.

Reference:

  * Uijeong Jang, Shuvomoy Das Gupta, Ernest K. Ryu, "Computer-Assisted Design of Accelerated Composite Optimization Methods: OptISTA," arXiv:2305.15704, 2023, [https://arxiv.org/abs/2305.15704]

# Required Arguments

  * `A`                                                 - forward operator

OR

  * `AHA`                                               - normal operator (as a keyword argument)

# Optional Keyword Arguments

  * `AHA`                                               - normal operator is optional if `A` is supplied
  * `reg::AbstractParameterizedRegularization`          - regularization term
  * `normalizeReg::AbstractRegularizationNormalization` - regularization normalization scheme; options are `NoNormalization()`, `MeasurementBasedNormalization()`, `SystemMatrixBasedNormalization()`
  * `rho::Real`                                         - step size for gradient step; the default is `0.95 / max_eigenvalue` as determined with power iterations.
  * `theta::Real`                                       - parameter for predictor-corrector step
  * `relTol::Real`                                      - tolerance for stopping criterion
  * `iterations::Int`                                   - maximum number of iterations
  * `verbose::Bool`                                     - print residual in each iteration

See also [`createLinearSolver`](@ref), [`solve!`](@ref).
