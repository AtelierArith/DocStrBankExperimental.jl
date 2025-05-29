API拡張。

```julia
struct Extensions <: VulkanSpec.Collection{VulkanSpec.SpecExtension}
```

  * `data::StructArrays.StructVector{VulkanSpec.SpecExtension, @NamedTuple{name::Vector{String}, type::Vector{VulkanSpec.ExtensionType}, requirements::Vector{Vector{String}}, support::Vector{VulkanSpec.ExtensionSupport}, author::Vector{Union{Nothing, String}}, symbols::Vector{Vector{Symbol}}, platform::Vector{VulkanSpec.PlatformType}, is_provisional::Vector{Bool}, promoted_to::Vector{Union{Nothing, VersionNumber, String}}, deprecated_by::Vector{Union{Nothing, String}}}, Int64}`
