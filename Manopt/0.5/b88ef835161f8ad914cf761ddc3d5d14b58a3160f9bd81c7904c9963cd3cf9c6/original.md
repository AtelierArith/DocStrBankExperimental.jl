```
default_stepsize(M::AbstractManifold, ams::AbstractManoptSolverState)
```

Returns the default [`Stepsize`](@ref) functor used when running the solver specified by the [`AbstractManoptSolverState`](@ref) `ams` running with an objective on the `AbstractManifold M`.
