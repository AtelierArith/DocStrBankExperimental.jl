```
remove_redundant_constraints!(constraints::AbstractVector{<:HalfSpace}; [backend]=nothing)
```

Remove the redundant constraints of a given list of linear constraints; the list is updated in-place.

### Input

  * `constraints` – list of constraints
  * `backend`     – (optional, default: `nothing`) the backend used to solve the                  linear program

### Output

`true` if the removal was successful and the list of constraints `constraints` is modified by removing the redundant constraints, and `false` only if the constraints are infeasible.

### Notes

Note that the result may be `true` even if the constraints are infeasible. For example, $x ≤ 0 && x ≥ 1$ will return `true` without removing any constraint. To check if the constraints are infeasible, use `isempty(HPolyhedron(constraints))`.

If `backend` is `nothing`, it defaults to `default_lp_solver(N)`.

### Algorithm

If there are `m` constraints in `n` dimensions, this function checks one by one if each of the `m` constraints is implied by the remaining ones.

To check if the `k`-th constraint is redundant, an LP is formulated using the constraints that have not yet been removed. If, at an intermediate step, it is detected that a subgroup of the constraints is infeasible, this function returns `false`. If the calculation finished successfully, this function returns `true`.

For details, see [Fukuda's Polyhedra FAQ](https://www.cs.mcgill.ca/~fukuda/soft/polyfaq/node24.html).
