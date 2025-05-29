```
partition(P::AbstractStateSpace; u, y, w=!u, z=!y)
```

Partition `P` into an [`ExtendedStateSpace`](@ref).

  * `u` indicates the indices of the controllable inputs.
  * `y` indicates the indices of the measurable outputs.
  * `w` indicates the indices of the disturbance inputs (uncontrollable), by default `w` is the complement of `u`.
  * `z` indicates the indices of the performance outputs (not neccesarily measurable), by default `z` is the complement of `y`.
