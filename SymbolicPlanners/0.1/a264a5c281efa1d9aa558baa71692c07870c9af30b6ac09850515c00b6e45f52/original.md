```julia
abstract type Solution
```

Abstract type for solutions to planning problems. Minimally, a `Solution` should define what action should be taken at a particular step `t`, or at a  particular `state`, by implementing [`get_action`](@ref).
