API定数は、通常Cで#defineを使用して定義されます。

```julia
struct Constants <: VulkanSpec.Collection{VulkanSpec.SpecConstant}
```

  * `data::StructArrays.StructVector{VulkanSpec.SpecConstant, @NamedTuple{name::Vector{Symbol}, value::Vector{Any}}, Int64}`
