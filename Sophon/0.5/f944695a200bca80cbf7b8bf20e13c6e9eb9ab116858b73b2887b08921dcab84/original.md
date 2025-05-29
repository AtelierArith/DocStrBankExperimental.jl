```
AdaptiveTraining(pde_weights, bcs_weights)
```

Adaptive weights for the loss functions. Here `pde_weights` and `bcs_weights` are functions that take in `(phi, x, θ)` and return the point-wise weights. Note that `bcs_weights` can be real numbers but they will be converted to functions that return the same numbers.
