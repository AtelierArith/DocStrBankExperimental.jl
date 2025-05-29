```
excess_solution_check!(path_result::PathResult,
                       F::RandomizedSystem,
                       newton_cache = NewtonCache(F.system))
```

Assigns to the [`PathResult`](@ref) `path_result` the `return_code` `:excess_solution` if the `path_result` is a solution of the randomized system `F` but not of the polynomial system underlying `F`. This is performed by using Newton's method for non-singular solutions and comparing the residuals of the solutions for singular solutions.
