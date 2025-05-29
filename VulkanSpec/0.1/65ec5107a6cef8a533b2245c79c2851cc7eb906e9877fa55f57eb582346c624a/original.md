API handle constructors.

```julia
struct Constructors <: VulkanSpec.Collection{VulkanSpec.CreateFunc}
```

  * `data::StructArrays.StructVector{VulkanSpec.CreateFunc, @NamedTuple{func::Vector{VulkanSpec.SpecFunc}, handle::Vector{VulkanSpec.SpecHandle}, create_info_struct::Vector{Union{Nothing, VulkanSpec.SpecStruct}}, create_info_param::Vector{Union{Nothing, VulkanSpec.SpecFuncParam}}, batch::Vector{Bool}}, Int64}`
