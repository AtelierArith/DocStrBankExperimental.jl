戻り値:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

引数:

  * `device::Device`
  * `initial_data::Ptr{Cvoid}`
  * `allocator::_AllocationCallbacks`: デフォルトは `C_NULL`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `flags::PipelineCacheCreateFlag`: デフォルトは `0`
  * `initial_data_size::UInt`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreatePipelineCache.html)

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
