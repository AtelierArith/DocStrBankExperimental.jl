```
get_gradient(amp::AbstractManoptProblem, p)
get_gradient!(amp::AbstractManoptProblem, X, p)
```

evaluate the gradient of an [`AbstractManoptProblem`](@ref) `amp` at the point `p`.

The evaluation is done in place of `X` for the `!`-variant.
