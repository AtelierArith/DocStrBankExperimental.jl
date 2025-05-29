Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

Arguments:

  * `device::Device`
  * `query_type::QueryType`
  * `query_count::UInt32`
  * `allocator::AllocationCallbacks`: defaults to `C_NULL`
  * `next::Any`: defaults to `C_NULL`
  * `flags::UInt32`: defaults to `0`
  * `pipeline_statistics::QueryPipelineStatisticFlag`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateQueryPool.html)

```julia
create_query_pool(
    device,
    query_type::Vulkan.QueryType,
    query_count::Integer;
    allocator,
    next,
    flags,
    pipeline_statistics
) -> ResultTypes.Result{Vulkan.QueryPool, Vulkan.VulkanError}

```
