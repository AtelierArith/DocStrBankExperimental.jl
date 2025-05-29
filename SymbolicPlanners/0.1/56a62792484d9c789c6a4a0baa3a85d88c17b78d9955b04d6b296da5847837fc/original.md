```julia
abstract type Heuristic
```

Abstract type for search heuristics, which estimate the distance from a  `State` to a goal specified by a [`Specification`](@ref). Once constructed,  a `heuristic` can be called on a domain, state, and specification, returning a  `Real` number (typically `Float32` for reduced memory usage).

```
heuristic(domain, state, spec; precompute=true)
```

Heuristics may precompute and store information that will be used repeatedly during search via the [`precompute!`](@ref) method. Evaluation of the heuristic on a state is defined by [`compute`](@ref).

If the `precompute` keyword argument is true when calling `heuristic` as a function, then [`precompute!`](@ref) will be called before [`compute`](@ref) is called to perform the heuristic evaluation.
