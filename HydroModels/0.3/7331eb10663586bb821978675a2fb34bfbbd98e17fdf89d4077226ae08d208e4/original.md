```
NeuralBucket{N} <: AbstractBucket
```

A recurrent neural network-based bucket for hydrological modeling that leverages Lux.jl's recurrence layers.

# Fields

  * `fluxes::Vector{<:AbstractHydroFlux}`: List of process functions to be applied.
  * `dfluxes::Vector{<:AbstractStateFlux}`: List of state derivative functions for state updates.
  * `func::Function`: Precompiled recurrent neural network function for efficient evaluation.
  * `infos::NamedTuple`: Metadata including input, output, state, parameter, and neural network names.

# Constructor

```julia
NeuralBucket(; name=nothing, fluxes, dfluxes)
```

  * `name::Union{Symbol,Nothing}`: Optional identifier for the bucket. Defaults to an autogenerated name.
  * `fluxes::Vector{<:AbstractHydroFlux}`: Required. Main computational elements.
  * `dfluxes::Vector{<:AbstractStateFlux}`: Required. State derivatives for recurrent updates.

# Usage Example

```julia
bucket = NeuralBucket(
    name = :neural_bucket,
    fluxes = [HydroFlux(...), NeuralFlux(...)],
    dfluxes = [StateFlux(...)]
)
```

The NeuralBucket differs from HydroBucket by using Lux.jl's recurrence layers to handle state updates over time, making it particularly suitable for sequence modeling tasks.
