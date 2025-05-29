```
FluxApproximator(; model, optimiser, usegpu=false)
```

Constructs an `FluxApproximator` object for reinforcement learning.

# Arguments

  * `model`: The model used for approximation.
  * `optimiser`: The optimizer used for updating the model.
  * `usegpu`: A boolean indicating whether to use GPU for computation. Default is `false`.

# Returns

An `FluxApproximator` object.
