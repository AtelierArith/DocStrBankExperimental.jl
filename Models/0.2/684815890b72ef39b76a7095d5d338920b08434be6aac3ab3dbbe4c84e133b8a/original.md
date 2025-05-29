```
predict(model::Model, inputs::AbstractMatrix)
predict(model::Model, inputs::AbstractVector{<:AbstractVector})
```

Predict targets for the provided the collection of `inputs` and [`Model`](@ref).

A [`Model`](@ref) subtype for which the `predict_input_type(model)` is  [`PointPredictInput`](@ref) will only need to implement a `predict` function that operates  on an `AbstractMatrix` of inputs.  

If the `estimate_type(model)` is [`PointEstimate`](@ref) then this function should return another `AbstractMatrix` in which each column contains the prediction for a single input.

If the `estimate_type(model)` is [`DistributionEstimate`](@ref) then this function should return a `AbstractVector{<:Distribution}`.
