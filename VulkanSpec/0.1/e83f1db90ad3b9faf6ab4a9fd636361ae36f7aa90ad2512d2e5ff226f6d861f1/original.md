API structure types.

```julia
struct Structs <: VulkanSpec.Collection{VulkanSpec.SpecStruct}
```

  * `data::StructArrays.StructVector{VulkanSpec.SpecStruct, @NamedTuple{name::Vector{Symbol}, type::Vector{VulkanSpec.StructType}, is_returnedonly::Vector{Bool}, extends::Vector{Vector{Symbol}}, members::Vector{StructArrays.StructVector{VulkanSpec.SpecStructMember}}}, Int64}`
