```
StopWhenChangeLess <: StoppingCriterion
```

stores a threshold when to stop looking at the norm of the change of the optimization variable from within a [`AbstractManoptSolverState`](@ref), i.e `get_iterate(o)`. For the storage a [`StoreStateAction`](@ref) is used

# Constructor

```
StopWhenChangeLess(
    M::AbstractManifold,
    ε::Float64;
    storage::StoreStateAction=StoreStateAction([:Iterate]),
    inverse_retraction_method::IRT=default_inverse_retraction_method(manifold)
)
```

initialize the stopping criterion to a threshold `ε` using the [`StoreStateAction`](@ref) `a`, which is initialized to just store `:Iterate` by default. You can also provide an inverse*retraction*method for the `distance` or a manifold to use its default inverse retraction.
