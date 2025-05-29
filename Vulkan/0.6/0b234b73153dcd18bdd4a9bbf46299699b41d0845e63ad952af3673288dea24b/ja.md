拡張: VK*NV*device*generated*commands

引数:

  * `device::Device`
  * `pipeline_bind_point::PipelineBindPoint`
  * `tokens::Vector{_IndirectCommandsLayoutTokenNV}`
  * `stream_strides::Vector{UInt32}`
  * `allocator::_AllocationCallbacks`: デフォルトは `C_NULL`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `flags::IndirectCommandsLayoutUsageFlagNV`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateIndirectCommandsLayoutNV.html)

```julia
IndirectCommandsLayoutNV(
    device,
    pipeline_bind_point::Vulkan.PipelineBindPoint,
    tokens::AbstractArray{Vulkan._IndirectCommandsLayoutTokenNV},
    stream_strides::AbstractArray;
    allocator,
    next,
    flags
) -> Vulkan.IndirectCommandsLayoutNV

```
