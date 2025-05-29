```
distinct_certified_solutions(F, S, p = nothing; threading::Bool = true, show_progress::Bool = true, certify_solution_kwargs...)
```

Return a `DistinctCertifiedSolutions` struct containing distinct certified solutions obtained from a vector of solutions `S` of a system `F`. Compared to `certify` this only keeps the distinct certified solutions and not all certificates. This in in particular useful if you want to merge multiple large solution sets into one set of distinct certified solutions.
