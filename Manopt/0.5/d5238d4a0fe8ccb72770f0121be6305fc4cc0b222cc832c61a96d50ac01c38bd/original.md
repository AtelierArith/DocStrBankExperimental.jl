```
update_storage!(a::AbstractStateAction, amp::AbstractManoptProblem, s::AbstractManoptSolverState)
```

Update the [`AbstractStateAction`](@ref) `a` internal values to the ones given on the [`AbstractManoptSolverState`](@ref) `s`. Optimized using the information from `amp`
