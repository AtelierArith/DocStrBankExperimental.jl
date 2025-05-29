引数:

  * `dynamic_states::Vector{DynamicState}`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `flags::UInt32`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineDynamicStateCreateInfo.html)

```julia
_PipelineDynamicStateCreateInfo(
    dynamic_states::AbstractArray;
    next,
    flags
) -> Vulkan._PipelineDynamicStateCreateInfo

```
