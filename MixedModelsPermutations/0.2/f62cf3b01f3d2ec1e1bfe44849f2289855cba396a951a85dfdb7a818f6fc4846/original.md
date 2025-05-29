```
MixedModels.residuals(model::LinearMixedModel, blups)
```

Compute the residuals of a mixed model, **ignoring blups**.

This a convenience function to allow [`nonparametricboostrap`](@ref) and [`permutation`](@ref) to always assume that the keyword argument `residual_method` is a two-argument method.

!!! warning
    This method is currently being pirated from MixedModels.jl and will probably be renamed or removed in a future release.

