```
Wing
```

Represents a wing composed of multiple sections with aerodynamic properties.

# Fields

  * `n_panels::Int16`: Number of panels in aerodynamic mesh
  * `n_groups::Int16`: Number of panel groups
  * `spanwise_distribution`::PanelDistribution: [PanelDistribution](@ref)
  * `spanwise_direction::MVec3`: Wing span direction vector
  * `sections::Vector{Section}`: Vector of wing sections, see: [Section](@ref)
  * `refined_sections::Vector{Section}`: Vector of refined wing sections, see: [Section](@ref)
  * `remove_nan::Bool`: Wether to remove the NaNs from interpolations or not
