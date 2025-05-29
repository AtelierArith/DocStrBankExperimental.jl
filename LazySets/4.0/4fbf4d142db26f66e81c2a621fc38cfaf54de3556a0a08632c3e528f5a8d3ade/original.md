```
isbounded(P::AbstractPolyhedron; [solver]=default_lp_solver(eltype(P)))
```

Check whether a polyhedron is bounded.

### Input

  * `P`       – polyhedron
  * `solver`  – (optional, default: `default_lp_solver(N)`) the backend used              to solve the linear program

### Output

`true` iff the polyhedron is bounded

### Algorithm

We first check if the polyhedron has more than `dim(P)` constraints, which is a necessary condition for boundedness.

If so, we check boundedness via `_isbounded_stiemke`.
