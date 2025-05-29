```julia
generate_solution(pb, orbit, period)

```

This function generates an initial guess for the solution of the problem `pb` based on the orbit `t -> orbit(t * period)` for t ∈ [0,1] and the `period`. Used also in `generate_ci_problem`.
