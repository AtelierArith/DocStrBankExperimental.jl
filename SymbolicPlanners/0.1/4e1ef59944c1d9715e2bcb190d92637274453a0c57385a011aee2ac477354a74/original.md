```
MultiSolution(solutions::Solution...)
MultiSolution(solutions::Tuple, [selector])
```

A combination of multiple [`Solution`](@ref)s, which are selected between according to a `selector` function `(solutions, [state]) -> sol` that returns the solution to use (which may depend on the current `state`). The `selector` default to always returning the first solution.
