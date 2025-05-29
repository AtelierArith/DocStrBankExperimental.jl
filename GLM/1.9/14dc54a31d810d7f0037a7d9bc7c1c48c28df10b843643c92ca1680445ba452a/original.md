```
predict(mm::LinearModel, newx::AbstractMatrix;
        interval::Union{Symbol,Nothing} = nothing, level::Real = 0.95)
```

If `interval` is `nothing` (the default), return a vector with the predicted values for model `mm` and new data `newx`. Otherwise, return a vector with the predicted values, as well as vectors with the lower and upper confidence bounds for a given `level` (0.95 equates alpha = 0.05). Valid values of `interval` are `:confidence` delimiting the  uncertainty of the predicted relationship, and `:prediction` delimiting estimated bounds for new data points.
