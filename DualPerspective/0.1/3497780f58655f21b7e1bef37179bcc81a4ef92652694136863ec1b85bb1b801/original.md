```
SSModel(kl::DPModel) -> SSModel
```

Create a self-scaled model from a Perspectron model.

# Arguments

  * `kl::DPModel`: The Perspectron model to wrap

# Description

This model is a container for `kl` and the augmented problem for the self-scaled model  in the variables (y,t).

The default starting point is `(y0, 1.0)`, where `y0` is the starting point of `kl`.
