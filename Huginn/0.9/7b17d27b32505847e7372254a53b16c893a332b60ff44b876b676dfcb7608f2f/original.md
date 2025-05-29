```
Prediction <: Simulation
```

A mutable struct that represents a prediction simulation.

# Fields

  * `model::Sleipnir.Model`: The model used for the prediction.
  * `glaciers::Vector{Sleipnir.AbstractGlacier}`: A vector of glaciers involved in the prediction.
  * `parameters::Sleipnir.Parameters`: The parameters used for the prediction.
  * `results::Vector{Results}`: A vector of results obtained from the prediction.
