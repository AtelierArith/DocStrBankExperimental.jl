SPIR-V capabilities.

```julia
struct CapabilitiesSPIRV <: VulkanSpec.Collection{VulkanSpec.SpecCapabilitySPIRV}
```

  * `data::StructArrays.StructVector{VulkanSpec.SpecCapabilitySPIRV, @NamedTuple{name::Vector{Symbol}, promoted_to::Vector{Union{Nothing, VersionNumber}}, enabling_extensions::Vector{Vector{String}}, enabling_features::Vector{Vector{VulkanSpec.FeatureCondition}}, enabling_properties::Vector{Vector{VulkanSpec.PropertyCondition}}}, Int64}`
