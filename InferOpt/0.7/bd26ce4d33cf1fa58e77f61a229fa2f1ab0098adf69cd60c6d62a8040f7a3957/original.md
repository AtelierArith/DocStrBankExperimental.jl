```
Interpolation <: AbstractOptimizationLayer
```

Piecewise-linear interpolation of a black-box optimizer.

# Fields

  * `maximizer`: underlying argmax function
  * `λ::Float64`: smoothing parameter (smaller = more faithful approximation, larger = more informative gradients)

Reference: [https://arxiv.org/abs/1912.02175](https://arxiv.org/abs/1912.02175)
