Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

Arguments:

  * `device::Device`
  * `create_info::PipelineCacheCreateInfo`
  * `allocator::AllocationCallbacks`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreatePipelineCache.html)

```julia
create_pipeline_cache(
    device,
    create_info::Vulkan.PipelineCacheCreateInfo;
    allocator
) -> ResultTypes.Result{Vulkan.PipelineCache, Vulkan.VulkanError}

```
