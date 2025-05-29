```
frank_wolfe(f, grad!, lmo, x0; ...)
```

Simplest form of the Frank-Wolfe algorithm. Returns a tuple `(x, v, primal, dual_gap, traj_data)` with:

  * `x` final iterate
  * `v` last vertex from the LMO
  * `primal` primal value `f(x)`
  * `dual_gap` final Frank-Wolfe gap
  * `traj_data` vector of trajectory information.
