```
MLJModelInterface.training_losses(model::M, report)
```

If `M` is an iterative model type which calculates training losses, implement this method to return an `AbstractVector` of the losses in historical order. If the model calculates scores instead, then the sign of the scores should be reversed.

The following trait overload is also required: `MLJModelInterface.supports_training_losses(::Type{<:M}) = true`.
