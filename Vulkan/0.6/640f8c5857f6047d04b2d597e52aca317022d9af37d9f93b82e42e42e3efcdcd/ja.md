拡張: VK*NV*device*generated*commands

引数:

  * `pipeline_bind_point::PipelineBindPoint`
  * `tokens::Vector{IndirectCommandsLayoutTokenNV}`
  * `stream_strides::Vector{UInt32}`
  * `next::Any`: デフォルトは `C_NULL`
  * `flags::IndirectCommandsLayoutUsageFlagNV`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkIndirectCommandsLayoutCreateInfoNV.html)

```julia
IndirectCommandsLayoutCreateInfoNV(
    pipeline_bind_point::Vulkan.PipelineBindPoint,
    tokens::AbstractArray,
    stream_strides::AbstractArray;
    next,
    flags
) -> Vulkan.IndirectCommandsLayoutCreateInfoNV

```
