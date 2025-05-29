Arguments:

  * `device::Device`
  * `initial_data::Ptr{Cvoid}`
  * `allocator::AllocationCallbacks`: defaults to `C_NULL`
  * `next::Any`: defaults to `C_NULL`
  * `flags::PipelineCacheCreateFlag`: defaults to `0`
  * `initial_data_size::UInt`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreatePipelineCache.html)

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
