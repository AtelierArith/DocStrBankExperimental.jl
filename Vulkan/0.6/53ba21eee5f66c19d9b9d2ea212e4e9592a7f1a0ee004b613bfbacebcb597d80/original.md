Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

Arguments:

  * `device::Device`
  * `initial_data::Ptr{Cvoid}`
  * `allocator::_AllocationCallbacks`: defaults to `C_NULL`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `flags::PipelineCacheCreateFlag`: defaults to `0`
  * `initial_data_size::UInt`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreatePipelineCache.html)

```julia
_create_pipeline_cache(
    device,
    initial_data::Ptr{Nothing};
    allocator,
    next,
    flags,
    initial_data_size
) -> ResultTypes.Result{Vulkan.PipelineCache, Vulkan.VulkanError}

```
