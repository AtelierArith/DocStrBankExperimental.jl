```
apply_forest(forest::Ensemble, features::AbstractMatrix; use_multithreading=false)
```

Apply learned model `forest` to `features`. Here `forest` is any `DecisionTree.Ensemble` instance, as returned, for example, by [`build_forest`](@ref).

# Keywords

  * `use_multithreading::Bool`: `true` to use multiple cores, if available. `false` by default.
