```
SubGradientMethodState <: AbstractManoptSolverState
```

stores option values for a [`subgradient_method`](@ref) solver

# Fields

  * `retraction_method`: the retraction to use within
  * `stepsize`:          ([`ConstantStepsize`](@ref)`(M)`) a [`Stepsize`](@ref)
  * `stop`:              ([`StopAfterIteration`](@ref)`(5000)``)a [`StoppingCriterion`](@ref)
  * `p`:                 (initial or current) value the algorithm is at
  * `p_star`:            optimal value (initialized to a copy of `p`.)
  * `X`:                 (`zero_vector(M, p)`) the current element from the possible subgradients at `p` that was last evaluated.

# Constructor

```
SubGradientMethodState(M::AbstractManifold, p; kwargs...)
```

with keywords for all fields besides `p_star` which obtains the same type as `p`. You can use `X=` to specify the type of tangent vector to use
