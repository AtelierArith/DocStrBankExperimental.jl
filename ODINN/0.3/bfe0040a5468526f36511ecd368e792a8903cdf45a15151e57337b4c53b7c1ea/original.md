```
function FunctionalInversion(
    model::Sleipnir.Model,
    glaciers::Vector{G},
    parameters::Sleipnir.Parameters
) where {G <: Sleipnir.AbstractGlacier}
```

Constructor for FunctionalInversion struct with glacier model information, glaciers, and parameters.

# Arguments

  * `model::Sleipnir.Model`: The model used for the simulation.
  * `glaciers::Vector{G}`: A vector of glaciers involved in the simulation.
  * `parameters::Sleipnir.Parameters`: The parameters used for the simulation.

# Returns

  * `FunctionalInversion`: A new instance of the FunctionalInversion struct.
