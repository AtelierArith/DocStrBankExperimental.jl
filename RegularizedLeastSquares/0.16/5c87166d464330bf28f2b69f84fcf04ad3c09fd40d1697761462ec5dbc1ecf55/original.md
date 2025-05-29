```
POGM(A; AHA = A'*A, reg = L1Regularization(zero(real(eltype(AHA)))), normalizeReg = NoNormalization(), iterations = 50, verbose = false, rho = 0.95 / power_iterations(AHA), theta = 1, sigma_fac = 1, relTol = eps(real(eltype(AHA))), restart = :none)
POGM( ; AHA = ,     reg = L1Regularization(zero(real(eltype(AHA)))), normalizeReg = NoNormalization(), iterations = 50, verbose = false, rho = 0.95 / power_iterations(AHA), theta = 1, sigma_fac = 1, relTol = eps(real(eltype(AHA))), restart = :none)
```

Creates a `POGM` object for the forward operator `A` or normal operator `AHA`. POGM has a 2x better worst-case bound than FISTA, but actual performance varies by application. It stores 3 extra intermediate variables the size of the image compared to FISTA. Only gradient restart scheme is implemented for now.

# References:

  * A.B. Taylor, J.M. Hendrickx, F. Glineur,   "Exact worst-case performance of first-order algorithms   for composite convex optimization," Arxiv:1512.07516, 2015,   SIAM J. Opt. 2017   [http://doi.org/10.1137/16m108104x]
  * Kim, D., & Fessler, J. A. (2018).   Adaptive Restart of the Optimized Gradient Method for Convex Optimization.   Journal of Optimization Theory and Applications, 178(1), 240–263.   [https://doi.org/10.1007/s10957-018-1287-4]

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
      * `sigma_fac::Real`                                   - parameter for decreasing γ-momentum ∈ [0,1]
      * `relTol::Real`                                      - tolerance for stopping criterion
      * `iterations::Int`                                   - maximum number of iterations
      * `restart::Symbol`                                   - `:none`, `:gradient` options for restarting
      * `verbose::Bool`                                     - print residual in each iteration

See also [`createLinearSolver`](@ref), [`solve!`](@ref).
