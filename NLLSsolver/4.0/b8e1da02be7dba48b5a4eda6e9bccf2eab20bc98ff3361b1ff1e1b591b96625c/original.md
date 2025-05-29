```
NLLSsolver.storecostscallback(store)
```

Generate a callback that stores per iteration information in `store` for later inspection.

# Example

Optimizing an NLLSsolver problem as follows:

```julia
    costs = Vector{Float64}()
    NLLSsolver.optimize!(problem, options, unfixed, storecostscallback(costs))
```

will cause the cost at the end of each iteration to be stored in the vector `costs`, while:

```julia
    costtrajectory = CostTrajectory()
    NLLSsolver.optimize!(problem, options, unfixed, storecostscallback(costtrajectory))
```

will cause the cost, step and optimization time at the end of each iteration to be stored in a [`CostTrajectory`](@ref) structure.

!!! note
    This method is useful for debugging, but will incur a performance penalty.

