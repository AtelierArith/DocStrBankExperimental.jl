```
remove_redundant_constraints(P::HPoly{N}; [backend]=nothing) where {N}
```

Remove the redundant constraints in a polyhedron in constraint representation.

### Input

  * `P`       – polyhedron
  * `backend` – (optional, default: `nothing`) the backend used to solve the              linear program

### Output

A polyhedron equivalent to `P` but with no redundant constraints, or an empty set if `P` is detected to be empty, which may happen if the constraints are infeasible.

### Notes

If `backend` is `nothing`, it defaults to `default_lp_solver(N)`.

### Algorithm

See `remove_redundant_constraints!(::AbstractVector{<:HalfSpace})` for details.
