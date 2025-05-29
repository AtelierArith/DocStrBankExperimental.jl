predict(path::RegularizationPath, newX::AbstractMatrix; kwargs...)

Predicted values for a selected segment of a regularization path.

# Examples

```julia
predict(path, newX; select=MinBIC())     # predict using BIC minimizing segment
```
