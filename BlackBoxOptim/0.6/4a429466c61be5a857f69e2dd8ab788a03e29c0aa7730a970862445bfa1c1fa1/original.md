```
bboptimize(problem[, x0, parameters::Associative; kwargs...])
```

Solve given optimization `problem`. Optionally a starting point `x0` can be specified.

See `setup_problem()` for the types of `problem` supported. In addition, the `problem` could be `OptController` containing the results of the previous optimization runs.

The optimization method parameters could be specified via `kwargs` or `parameters` arguments.

Returns `OptimizationResults` instance.

See also `bbsetup()` and [`BlackBoxOptim.OptRunController`](@ref) for a full list of supported parameters.
