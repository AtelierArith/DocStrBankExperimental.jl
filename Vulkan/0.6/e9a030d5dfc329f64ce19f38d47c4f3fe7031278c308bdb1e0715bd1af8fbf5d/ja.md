拡張: VK*NV*device*generated*commands

引数:

  * `pipeline_bind_point::PipelineBindPoint`
  * `tokens::Vector{_IndirectCommandsLayoutTokenNV}`
  * `stream_strides::Vector{UInt32}`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `flags::IndirectCommandsLayoutUsageFlagNV`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkIndirectCommandsLayoutCreateInfoNV.html)

```julia
_IndirectCommandsLayoutCreateInfoNV(
    pipeline_bind_point::Vulkan.PipelineBindPoint,
    tokens::AbstractArray,
    stream_strides::AbstractArray;
    next,
    flags
) -> Vulkan._IndirectCommandsLayoutCreateInfoNV

```
