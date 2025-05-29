```
forward_trajectory(imm::IMM, u, y, p = parameters(imm); interact = true)
```

When performing batch filtering using an [`IMM`](@ref) filter, one may

  * Override the `interact` parameter of the filter
  * Access the mode probabilities along the trajectory as the `sol.extra` field. This is a matrix of size `(n_modes, T)` where `T` is the length of the trajectory (length of `u` and `y`).

The returned solution object is of type [`KalmanFilteringSolution`](@ref) and has the following fields:
