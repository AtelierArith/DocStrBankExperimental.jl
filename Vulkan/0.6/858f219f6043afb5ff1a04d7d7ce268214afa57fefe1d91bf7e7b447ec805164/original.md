Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

Arguments:

  * `device::Device`
  * `create_info::_QueryPoolCreateInfo`
  * `allocator::_AllocationCallbacks`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateQueryPool.html)

```julia
_create_query_pool(
    device,
    create_info::Vulkan._QueryPoolCreateInfo;
    allocator
) -> ResultTypes.Result{Vulkan.QueryPool, Vulkan.VulkanError}

```
