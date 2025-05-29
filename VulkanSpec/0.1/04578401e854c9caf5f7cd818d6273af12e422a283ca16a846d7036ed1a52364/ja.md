API ビットマスク。

```julia
struct Bitmasks <: VulkanSpec.Collection{VulkanSpec.SpecBitmask}
```

  * `data::StructArrays.StructVector{VulkanSpec.SpecBitmask, @NamedTuple{name::Vector{Symbol}, bits::Vector{StructArrays.StructVector{VulkanSpec.SpecBit}}, combinations::Vector{StructArrays.StructVector{VulkanSpec.SpecBitCombination}}, width::Vector{Integer}}, Int64}`
