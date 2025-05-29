predict(m::RegularizedModel, newX::AbstractMatrix; kwargs...)

Predicted values using a selected segment of a regularization path.

# Examples

```julia
m = fit(LassoModel, X, y; select=MinBIC())
predict(m, newX)     # predict using BIC minimizing segment
```
