API constants, usually defined in C with #define.

```julia
struct Constants <: VulkanSpec.Collection{VulkanSpec.SpecConstant}
```

  * `data::StructArrays.StructVector{VulkanSpec.SpecConstant, @NamedTuple{name::Vector{Symbol}, value::Vector{Any}}, Int64}`
