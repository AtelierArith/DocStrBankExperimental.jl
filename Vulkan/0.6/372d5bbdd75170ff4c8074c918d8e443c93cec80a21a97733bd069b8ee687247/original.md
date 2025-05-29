SPIR-V capability with information regarding various requirements to consider it enabled.

```julia
struct SpecCapabilitySPIRV
```

  * `name::Symbol`: Name of the SPIR-V capability.
  * `promoted_to::Union{Nothing, VersionNumber}`: Core version of the Vulkan API in which the SPIR-V capability was promoted, if promoted.
  * `enabling_extensions::Vector{String}`: Vulkan extensions that implicitly enable the SPIR-V capability.
  * `enabling_features::Vector{Vulkan.FeatureCondition}`: Vulkan features that implicitly enable the SPIR-V capability.
  * `enabling_properties::Vector{Vulkan.PropertyCondition}`: Vulkan properties that implicitly enable the SPIR-V capability.
