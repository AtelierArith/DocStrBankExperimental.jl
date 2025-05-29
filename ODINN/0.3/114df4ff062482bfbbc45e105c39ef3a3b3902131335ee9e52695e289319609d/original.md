```
Inversion <: Simulation
```

A mutable struct that represents an inversion simulation.

# Fields

  * `model::Sleipnir.Model`: The model used for the inversion.
  * `glaciers::Vector{Sleipnir.AbstractGlacier}`: A vector of glaciers involved in the inversion.
  * `parameters::Sleipnir.Parameters`: The parameters used for the inversion.
  * `inversion::Vector{InversionResults}`: A vector of results from the inversion.
