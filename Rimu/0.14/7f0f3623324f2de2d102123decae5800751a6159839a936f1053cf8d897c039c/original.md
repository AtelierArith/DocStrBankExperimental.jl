```
FCIQMC(; kwargs...) <: PMCAlgorithm
```

Algorithm for the full configuration interaction quantum Monte Carlo (FCIQMC) method. The default algorithm for [`ProjectorMonteCarloProblem`](@ref).

# Keyword arguments and defaults:

  * `shift_strategy = DoubleLogUpdate(; targetwalkers = 1_000, ζ = 0.08,   ξ = ζ^2/4)`: How to update the `shift`.
  * `time_step_strategy = ConstantTimeStep()`: Adjust time step or not.

See also [`ProjectorMonteCarloProblem`](@ref), [`ShiftStrategy`](@ref), [`TimeStepStrategy`](@ref), [`DoubleLogUpdate`](@ref), [`ConstantTimeStep`](@ref).
