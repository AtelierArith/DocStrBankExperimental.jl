```
SplitBregman(A; AHA = A'*A, precon = Identity(), reg = L1Regularization(zero(real(eltype(AHA)))), regTrafo = opEye(eltype(AHA), size(AHA,1)), normalizeReg = NoNormalization(), rho = 1e-1, iterations = 10, iterationsInner = 10, iterationsCG = 10, absTol = eps(real(eltype(AHA))), relTol = eps(real(eltype(AHA))), tolInner = 1e-5, verbose = false)
SplitBregman( ; AHA = ,     precon = Identity(), reg = L1Regularization(zero(real(eltype(AHA)))), regTrafo = opEye(eltype(AHA), size(AHA,1)), normalizeReg = NoNormalization(), rho = 1e-1, iterations = 10, iterationsInner = 10, iterationsCG = 10, absTol = eps(real(eltype(AHA))), relTol = eps(real(eltype(AHA))), tolInner = 1e-5, verbose = false)
```

Creates a `SplitBregman` object for the forward operator `A` or normal operator `AHA`.

# Required Arguments

  * `A`                                                 - forward operator

OR

  * `AHA`                                               - normal operator (as a keyword argument)

# Optional Keyword Arguments

  * `AHA`                                               - normal operator is optional if `A` is supplied
  * `precon`                                            - preconditionner for the internal CG algorithm
  * `reg::AbstractParameterizedRegularization`          - regularization term; can also be a vector of regularization terms
  * `regTrafo`                                          - transformation to a space in which `reg` is applied; if `reg` is a vector, `regTrafo` has to be a vector of the same length. Use `opEye(eltype(AHA), size(AHA,1))` if no transformation is desired.
  * `normalizeReg::AbstractRegularizationNormalization` - regularization normalization scheme; options are `NoNormalization()`, `MeasurementBasedNormalization()`, `SystemMatrixBasedNormalization()`
  * `rho::Real`                                         - weights for condition on regularized variables; can also be a vector for multiple regularization terms
  * `iterations::Int`                              - maximum number of outer iterations. Set to 1 for unconstraint split Bregman (equivalent to ADMM)
  * `iterationsInner::Int`                              - maximum number of inner iterations
  * `iterationsCG::Int`                                 - maximum number of (inner) CG iterations
  * `absTol::Real`                                      - absolute tolerance for stopping criterion
  * `relTol::Real`                                      - relative tolerance for stopping criterion
  * `tolInner::Real`                                    - relative tolerance for CG stopping criterion
  * `verbose::Bool`                                     - print residual in each iteration

This algorithm solves the constraint problem (Eq. (4.7) in [Tom Goldstein and Stanley Osher](https://doi.org/10.1137/080725891)), i.e. `||R(x)||₁` such that `||Ax -b||₂² < σ²`. In order to solve the unconstraint problem (Eq. (4.8) in [Tom Goldstein and Stanley Osher](https://doi.org/10.1137/080725891)), i.e. `||Ax -b||₂² + λ ||R(x)||₁`, you can either set `iterations=1` or use ADMM instead, which is equivalent (`iterations=1` in SplitBregman in implied in ADMM and the SplitBregman variable `iterationsInner` is simply called `iterations` in ADMM)

Like ADMM, SplitBregman differs from ISTA-type algorithms in the sense that the proximal operation is applied separately from the transformation to the space in which the penalty is applied. This is reflected by the interface which has `reg` and `regTrafo` as separate arguments. E.g., for a TV penalty, you should NOT set `reg=TVRegularization`, but instead use `reg=L1Regularization(λ), regTrafo=RegularizedLeastSquares.GradientOp(Float64; shape=(Nx,Ny,Nz))`.

See also [`createLinearSolver`](@ref), [`solve!`](@ref).
