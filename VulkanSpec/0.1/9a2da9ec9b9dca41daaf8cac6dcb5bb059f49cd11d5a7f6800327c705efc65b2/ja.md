APIの列挙値、ビットマスクを除く。

```julia
struct Enums <: VulkanSpec.Collection{VulkanSpec.SpecEnum}
```

  * `data::StructArrays.StructVector{VulkanSpec.SpecEnum, @NamedTuple{name::Vector{Symbol}, enums::Vector{StructArrays.StructVector{VulkanSpec.SpecConstant}}}, Int64}`
