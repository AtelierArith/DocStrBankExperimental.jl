Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

Arguments:

  * `device::Device`
  * `create_info::QueryPoolCreateInfo`
  * `allocator::AllocationCallbacks`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateQueryPool.html)

```julia
create_query_pool(
    device,
    create_info::Vulkan.QueryPoolCreateInfo;
    allocator
) -> ResultTypes.Result{Vulkan.QueryPool, Vulkan.VulkanError}

```
