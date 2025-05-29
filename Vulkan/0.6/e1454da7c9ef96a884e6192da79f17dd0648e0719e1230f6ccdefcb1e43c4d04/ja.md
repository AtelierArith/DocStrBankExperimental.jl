引数:

  * `device::Device`
  * `initial_data::Ptr{Cvoid}`
  * `allocator::AllocationCallbacks`: デフォルトは `C_NULL`
  * `next::Any`: デフォルトは `C_NULL`
  * `flags::PipelineCacheCreateFlag`: デフォルトは `0`
  * `initial_data_size::UInt`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreatePipelineCache.html)

```julia
PipelineCache(
    device,
    initial_data::Ptr{Nothing};
    allocator,
    next,
    flags,
    initial_data_size
) -> Vulkan.PipelineCache

```
