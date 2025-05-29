Arguments:

  * `dynamic_states::Vector{DynamicState}`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `flags::UInt32`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineDynamicStateCreateInfo.html)

```julia
_PipelineDynamicStateCreateInfo(
    dynamic_states::AbstractArray;
    next,
    flags
) -> Vulkan._PipelineDynamicStateCreateInfo

```
