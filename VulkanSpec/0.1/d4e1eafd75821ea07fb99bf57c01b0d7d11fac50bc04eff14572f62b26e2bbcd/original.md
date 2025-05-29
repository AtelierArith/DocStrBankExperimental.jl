Specification for a function.

```julia
struct SpecFunc <: VulkanSpec.Spec
```

  * `name::Symbol`: Name of the function.
  * `type::VulkanSpec.FunctionType`: [`FunctionType`](@ref) classification.
  * `return_type::Union{Nothing, Expr, Symbol}`: Return type (void if `Nothing`).
  * `render_pass_compatibility::Vector{VulkanSpec.RenderPassRequirement}`: Whether the function can be executed inside a render pass, outside, or both. Empty if not specified, in which case it is equivalent to both inside and outside.
  * `queue_compatibility::Vector{VulkanSpec.QueueType}`: Type of queues on which the function can be executed. Empty if not specified, in which case it is equivalent to being executable on all queues.
  * `params::StructArrays.StructVector{VulkanSpec.SpecFuncParam}`: Function parameters.
  * `success_codes::Vector{Symbol}`
  * `error_codes::Vector{Symbol}`
