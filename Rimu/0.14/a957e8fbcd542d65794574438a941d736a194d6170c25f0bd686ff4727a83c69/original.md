```
ShiftStrategy
```

Abstract type for defining the strategy for controlling the norm, potentially by updating the `shift`. Passed as a parameter to [`ProjectorMonteCarloProblem`](@ref) or to [`FCIQMC`](@ref).

## Implemented strategies:

  * [`DontUpdate`](@ref)
  * [`DoubleLogUpdate`](@ref) - default in [`ProjectorMonteCarloProblem()`](@ref)
  * [`LogUpdate`](@ref)
  * [`LogUpdateAfterTargetWalkers`](@ref) - FCIQMC standard
  * [`DoubleLogUpdateAfterTargetWalkers`](@ref)

# Extended help

Internally To implement a custom strategy, define a new subtype of `Rimu.ShiftStrategy` and implement methods for:

  * [`Rimu.update_shift_parameters!`](@ref) - to update the `shift_parameters`
  * [`Rimu.initialise_shift_parameters`](@ref) - (optional) to initialise and construct a   custom implementation of the `shift_parameters`. The default implementation is   [`Rimu.DefaultShiftParameters`](@ref).
