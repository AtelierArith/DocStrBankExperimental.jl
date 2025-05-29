```
StopWhenAllLanczosVectorsUsed <: StoppingCriterion
```

When an inner iteration has used up all Lanczos vectors, then this stopping criterion is a fallback / security stopping criterion to not access a non-existing field in the array allocated for vectors.

Note that this stopping criterion (for now) is only implemented for the case that an [`AdaptiveRegularizationState`](@ref) when using a [`LanczosState`](@ref) subsolver

# Fields

  * `maxLanczosVectors`: maximal number of Lanczos vectors
  * `at_iteration` indicates at which iteration (including `i=0`) the stopping criterion was fulfilled and is `-1` while it is not fulfilled.

# Constructor

```
StopWhenAllLanczosVectorsUsed(maxLancosVectors::Int)
```
