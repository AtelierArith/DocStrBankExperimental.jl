```
minimize(f, (x_left, x_right); atol)
```

Minimize a convex function `f` on the interval `[x_left, x_right]`.

# Arguments

  * f: Function that should be minimized, does not have to be differentiable.
  * atol: Search tolereance, such that `isapprox(true_minimizer, sol.minimizer, atol=atol)`

will hold.
