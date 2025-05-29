Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

Arguments:

  * `device::Device`
  * `create_info::_PipelineCacheCreateInfo`
  * `allocator::_AllocationCallbacks`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreatePipelineCache.html)

```julia
_create_pipeline_cache(
    device,
    create_info::Vulkan._PipelineCacheCreateInfo;
    allocator
) -> ResultTypes.Result{Vulkan.PipelineCache, Vulkan.VulkanError}

```
