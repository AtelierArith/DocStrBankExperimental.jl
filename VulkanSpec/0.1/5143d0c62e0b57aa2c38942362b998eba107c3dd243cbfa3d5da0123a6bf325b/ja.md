SPIR-V 拡張。

```julia
struct ExtensionsSPIRV <: VulkanSpec.Collection{VulkanSpec.SpecExtensionSPIRV}
```

  * `data::StructArrays.StructVector{VulkanSpec.SpecExtensionSPIRV, @NamedTuple{name::Vector{String}, promoted_to::Vector{Union{Nothing, VersionNumber}}, enabling_extensions::Vector{Vector{String}}}, Int64}`
