```
PostStepStrategy
```

Subtypes of `PostStepStrategy` can be used to perform arbitrary computation on a single state after an FCIQMC step is finished and report the results.

# Implemented strategies:

  * [`ProjectedEnergy`](@ref)
  * [`Projector`](@ref)
  * [`SignCoherence`](@ref)
  * [`WalkerLoneliness`](@ref)
  * [`Timer`](@ref)

Note: A tuple of multiple strategies can be passed to [`ProjectorMonteCarloProblem`](@ref). In that case, all reported column names must be distinct.

# Interface:

A subtype of this type must implement [`post_step_action(::PostStepStrategy, ::SingleState, step::Int)`](@ref).
