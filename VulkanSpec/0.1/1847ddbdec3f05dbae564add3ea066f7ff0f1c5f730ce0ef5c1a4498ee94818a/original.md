API functions.

```julia
struct Functions <: VulkanSpec.Collection{VulkanSpec.SpecFunc}
```

  * `data::StructArrays.StructVector{VulkanSpec.SpecFunc, @NamedTuple{name::Vector{Symbol}, type::Vector{VulkanSpec.FunctionType}, return_type::Vector{Union{Nothing, Expr, Symbol}}, render_pass_compatibility::Vector{Vector{VulkanSpec.RenderPassRequirement}}, queue_compatibility::Vector{Vector{VulkanSpec.QueueType}}, params::Vector{StructArrays.StructVector{VulkanSpec.SpecFuncParam}}, success_codes::Vector{Vector{Symbol}}, error_codes::Vector{Vector{Symbol}}}, Int64}`
