```
get_subgradient(amp::AbstractManoptProblem, p)
get_subgradient!(amp::AbstractManoptProblem, X, p)
```

evaluate the subgradient of an [`AbstractManoptProblem`](@ref) `amp` at point `p`.

The evaluation is done in place of `X` for the `!`-variant. The result might not be deterministic, *one* element of the subdifferential is returned.
