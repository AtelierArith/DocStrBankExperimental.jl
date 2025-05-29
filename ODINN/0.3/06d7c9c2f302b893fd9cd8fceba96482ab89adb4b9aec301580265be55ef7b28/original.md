```
Inversion(model::Sleipnir.Model, glaciers::Vector{G}, parameters::Sleipnir.Parameters) where {G <: Sleipnir.AbstractGlacier}
```

Create an `Inversion` object using the provided model, glaciers, and parameters.

# Arguments

  * `model::Sleipnir.Model`: The model to be used for the inversion.
  * `glaciers::Vector{G}`: A vector of glaciers, where each glacier is a subtype of `Sleipnir.AbstractGlacier`.
  * `parameters::Sleipnir.Parameters`: The parameters to be used for the inversion.

# Returns

  * `inversion`: An `Inversion` object initialized with the provided model, glaciers, and parameters.
