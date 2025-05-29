```
underapproximate(X::LazySet, ::Type{<:Hyperrectangle};
                 solver=nothing) where {N}
```

Underapproximate a convex polygon with a hyperrectangle of maximal area.

### Input

  * `X`              – convex polygon
  * `Hyperrectangle` – type for dispatch
  * `solver`         – (optional; default: `nothing`) nonlinear solver; if                     `nothing`, `default_nln_solver(N)` will be used

### Output

A hyperrectangle underapproximation with maximal area.

### Notes

The implementation only works for 2D sets, but the algorithm can be generalized.

Due to numerical issues, the result may be slightly outside the set.

### Algorithm

The algorithm is taken from [Behroozi19; Theorem 17](@citet) and solves a convex program (in fact a linear program with nonlinear objective). (The objective is modified to an equivalent version due to solver issues.)
