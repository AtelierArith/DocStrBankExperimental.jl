API handle destructors.

```julia
struct Destructors <: VulkanSpec.Collection{VulkanSpec.DestroyFunc}
```

  * `data::StructArrays.StructVector{VulkanSpec.DestroyFunc, @NamedTuple{func::Vector{VulkanSpec.SpecFunc}, handle::Vector{VulkanSpec.SpecHandle}, destroyed_param::Vector{VulkanSpec.SpecFuncParam}, batch::Vector{Bool}}, Int64}`
