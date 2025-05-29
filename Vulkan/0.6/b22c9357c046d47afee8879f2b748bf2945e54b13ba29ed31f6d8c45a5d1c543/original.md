Arguments:

  * `dynamic_states::Vector{DynamicState}`
  * `next::Any`: defaults to `C_NULL`
  * `flags::UInt32`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineDynamicStateCreateInfo.html)

```julia
PipelineDynamicStateCreateInfo(
    dynamic_states::AbstractArray;
    next,
    flags
) -> Vulkan.PipelineDynamicStateCreateInfo

```
