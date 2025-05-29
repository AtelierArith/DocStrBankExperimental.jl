```
predict(mm::AbstractGLM, newX::AbstractMatrix; offset::FPVector=eltype(newX)[],
        interval::Union{Symbol,Nothing}=nothing, level::Real = 0.95,
        interval_method::Symbol = :transformation)
```

Return the predicted response of model `mm` from covariate values `newX` and, optionally, an `offset`.

If `interval=:confidence`, also return upper and lower bounds for a given coverage `level`. By default (`interval_method = :transformation`) the intervals are constructed by applying the inverse link to intervals for the linear predictor. If `interval_method = :delta`, the intervals are constructed by the delta method, i.e., by linearization of the predicted response around the linear predictor. The `:delta` method intervals are symmetric around the point estimates, but do not respect natural parameter constraints (e.g., the lower bound for a probability could be negative).
