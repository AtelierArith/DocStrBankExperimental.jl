API flags.

```julia
struct Flags <: VulkanSpec.Collection{VulkanSpec.SpecFlag}
```

  * `data::StructArrays.StructVector{VulkanSpec.SpecFlag, @NamedTuple{name::Vector{Symbol}, typealias::Vector{Symbol}, bitmask::Vector{Union{Nothing, VulkanSpec.SpecBitmask}}}, Int64}`
