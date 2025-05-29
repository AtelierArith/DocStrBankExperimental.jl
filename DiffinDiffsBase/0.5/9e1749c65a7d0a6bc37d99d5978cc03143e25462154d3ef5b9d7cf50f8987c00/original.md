```
UnspecifiedParallel{C,S} <: AbstractParallel{C,S}
```

A parallel trends assumption (PTA) without explicitly specified relations across treatment groups. See also [`unspecifiedpr`](@ref).

With this parallel type, operations for complying with a PTA are suppressed. This is useful, for example, when the user-provided regressors and sample restrictions need to be accepted without any PTA-specific alteration.

# Fields

  * `c::C`: an instance of [`ParallelCondition`](@ref).
  * `s::S`: an instance of [`ParallelStrength`](@ref).
