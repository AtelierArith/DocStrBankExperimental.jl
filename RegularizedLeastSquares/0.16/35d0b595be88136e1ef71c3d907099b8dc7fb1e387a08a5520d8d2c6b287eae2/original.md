```
Kaczmarz(A; reg = L2Regularization(0), normalizeReg = NoNormalization(), randomized=false, subMatrixFraction=0.15, shuffleRows=false, seed=1234, iterations=10)
```

Creates a Kaczmarz object for the forward operator `A`.

# Required Arguments

  * `A`                                                 - forward operator

# Optional Keyword Arguments

  * `reg::AbstractParameterizedRegularization`          - regularization term
  * `normalizeReg::AbstractRegularizationNormalization` - regularization normalization scheme; options are `NoNormalization()`, `MeasurementBasedNormalization()`, `SystemMatrixBasedNormalization()`
  * `randomized::Bool`                                    - randomize Kacmarz algorithm
  * `subMatrixFraction::Real`                             - fraction of rows used in randomized Kaczmarz algorithm
  * `shuffleRows::Bool`                                   - randomize Kacmarz algorithm
  * `seed::Int`                                           - seed for randomized algorithm
  * `iterations::Int`                                     - number of iterations

See also [`createLinearSolver`](@ref), [`solve!`](@ref).
