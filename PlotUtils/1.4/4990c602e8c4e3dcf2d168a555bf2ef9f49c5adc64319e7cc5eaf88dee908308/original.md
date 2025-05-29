```
adapted_grid(f, minmax::Tuple{Number, Number}; max_recursions = 7, max_curvature = 0.01, n_points = 31)
```

Computes a grid `x` on the interval [minmax[1], minmax[2]] so that `plot(f, x)` gives a smooth "nice" plot. The method used is to create an uniform grid with `n_points` initial points and refine intervals where the second derivative is approximated to be large. When an interval becomes "straight enough" it is no longer divided. Functions are evaluated at the end points of the intervals.

The parameter `max_recursions` computes how many times each interval is allowed to be refined while `max_curvature` specifies below which value of the curvature an interval does not need to be refined further.
