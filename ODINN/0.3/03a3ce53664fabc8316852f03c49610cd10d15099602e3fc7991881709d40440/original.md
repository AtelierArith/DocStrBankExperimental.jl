```
mutable struct FunctionalInversion <: Simulation
```

An object representing a functional inversion simulation (i.e. the inversion of a function using some data-driven regressor).

# Fields

  * `model::Sleipnir.Model`: The model used for the simulation.
  * `glaciers::Vector{Sleipnir.AbstractGlacier}`: A vector of glaciers involved in the simulation.
  * `parameters::Sleipnir.Parameters`: The parameters used for the simulation.
  * `results::Vector{Results}`: A vector to store the results of the simulation.
