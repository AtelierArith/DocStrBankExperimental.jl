```
excess_solution_check(F::RandomizedSystem)
```

Returns a function `λ(::PathResult)` which performs the excess solution check. The call `excess_solution_check(F)(path_result)` is identical to `excess_solution_check!(F, path_result)`. See also [`excess_solution_check!`](@ref).
