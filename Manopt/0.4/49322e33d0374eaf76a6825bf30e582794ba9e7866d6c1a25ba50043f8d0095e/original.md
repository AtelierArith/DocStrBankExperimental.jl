```
DebugSolverState <: AbstractManoptSolverState
```

The debug state appends debug to any state, they act as a decorator pattern. Internally a dictionary is kept that stores a [`DebugAction`](@ref) for several occasions using a `Symbol` as reference.

The original options can still be accessed using the [`get_state`](@ref) function.

# Fields

  * `options`:         the options that are extended by debug information
  * `debugDictionary`: a `Dict{Symbol,DebugAction}` to keep track of Debug for different actions

# Constructors

```
DebugSolverState(o,dA)
```

construct debug decorated options, where `dD` can be

  * a [`DebugAction`](@ref), then it is stored within the dictionary at `:Iteration`
  * an `Array` of [`DebugAction`](@ref)s.
  * a `Dict{Symbol,DebugAction}`.
  * an Array of Symbols, String and an Int for the [`DebugFactory`](@ref)
