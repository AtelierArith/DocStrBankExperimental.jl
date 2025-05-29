```
remove_redundant_constraints(constraints::AbstractVector{<:HalfSpace}; backend=nothing)
```

Remove the redundant constraints of a given list of linear constraints.

### Input

  * `constraints` – list of constraints
  * `backend`     – (optional, default: `nothing`) the backend used to solve the                  linear program

### Output

The list of constraints with the redundant ones removed, or an empty list if the constraints are infeasible.

### Notes

If `backend` is `nothing`, it defaults to `default_lp_solver(N)`.

### Algorithm

See `[remove_redundant_constraints!(::AbstractVector{<:HalfSpace})](@ref)` for details.
