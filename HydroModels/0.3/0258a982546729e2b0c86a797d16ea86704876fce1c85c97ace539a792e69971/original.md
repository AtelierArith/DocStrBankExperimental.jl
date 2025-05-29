```
HydroModel{N} <: AbstractModel
```

Represents a complete hydrological model that integrates multiple components for simulating water processes.

# Fields

  * `components::Vector{<:AbstractComponent}`: Hydrological computation components (e.g., `HydroBucket`, `UnitHydrograph`).
  * `infos::NamedTuple`: Metadata including variable names (inputs, outputs, states, params, nns) aggregated from components.
  * `_varindices::AbstractVector{AbstractVector{Int}}`: Input variable indices for each component, determined automatically during construction to manage data flow.
  * `_outputindices::AbstractVector{Int}`: Indices used to select and order the final model outputs from all internal variables.

# Constructor

```julia
HydroModel(; components::Vector{<:AbstractComponent}, name::Union{Symbol,Nothing}=nothing)
```

  * `components`: Required. A vector containing the different model components.
  * `name`: Optional symbol to identify the model. If `nothing`, a unique name is generated.

# Usage Example

```julia
# Assuming bucket1 and routing1 are predefined AbstractComponent instances
model = HydroModel(
    name = :simple_catchment,
    components = [bucket1, routing1]
)

# Simulate the model
# output = model(input_data, parameters)
```

# Notes

  * The type parameter `N` encodes the model `name` at the type level for potential dispatch optimizations.
  * Component connections and variable routing (`_varindices`, `_outputindices`) are handled automatically.
  * The constructed `model` object is callable to perform simulations (see the function call operator documentation for details).
