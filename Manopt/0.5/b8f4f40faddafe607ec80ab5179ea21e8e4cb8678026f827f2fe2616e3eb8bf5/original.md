```
RecordSolverState <: AbstractManoptSolverState
```

append to any [`AbstractManoptSolverState`](@ref) the decorator with record capability, Internally a dictionary is kept that stores a [`RecordAction`](@ref) for several concurrent modes using a `Symbol` as reference. The default mode is `:Iteration`, which is used to store information that is recorded during the iterations. RecordActions might be added to `:Start` or `:Stop` to record values at the beginning or for the stopping time point, respectively

The original options can still be accessed using the [`get_state`](@ref) function.

# Fields

  * `options`          the options that are extended by debug information
  * `recordDictionary` a `Dict{Symbol,RecordAction}` to keep track of all different recorded values

# Constructors

```
RecordSolverState(o,dR)
```

construct record decorated [`AbstractManoptSolverState`](@ref), where `dR` can be

  * a [`RecordAction`](@ref), then it is stored within the dictionary at `:Iteration`
  * an `Array` of [`RecordAction`](@ref)s, then it is stored as a `recordDictionary`(@ref).
  * a `Dict{Symbol,RecordAction}`.
