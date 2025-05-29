# Extended help

```
minkowski_sum(P1::VPolytope, P2::VPolytope;
              [apply_convex_hull]=true,
              [backend]=nothing,
              [solver]=nothing)
```

### Input

  * `apply_convex_hull` – (optional, default: `true`) if `true`, post-process the                        pairwise sums using a convex-hull algorithm
  * `backend`           – (optional, default: `nothing`) the backend for                        polyhedral computations used to post-process with a                        convex hull; see `default_polyhedra_backend(P1)`
  * `solver`            – (optional, default: `nothing`) the backend used to                        solve the linear program; see                        `default_lp_solver_polyhedra(N)`

### Algorithm

The resulting polytope in vertex representation consists of the vertices corresponding to the convex hull of the sum of all possible sums of vertices of `P1` and `P2`.
