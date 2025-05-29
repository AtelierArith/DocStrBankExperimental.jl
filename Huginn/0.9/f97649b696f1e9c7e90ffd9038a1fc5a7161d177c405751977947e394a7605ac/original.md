```
Prediction(model::Sleipnir.Model, glaciers::Vector{G}, parameters::Sleipnir.Parameters) where {G <: Sleipnir.AbstractGlacier}
```

Create a `Prediction` object using the given model, glaciers, and parameters.

# Arguments

  * `model::Sleipnir.Model`: The model used for prediction.
  * `glaciers::Vector{G}`: A vector of glacier objects, where each glacier is a subtype of `Sleipnir.AbstractGlacier`.
  * `parameters::Sleipnir.Parameters`: The parameters used for the prediction.

# Returns

  * `Prediction`: A `Prediction` object based on the input values.
