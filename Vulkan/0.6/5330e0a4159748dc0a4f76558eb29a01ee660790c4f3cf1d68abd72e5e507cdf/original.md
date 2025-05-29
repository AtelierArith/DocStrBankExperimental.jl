Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

Arguments:

  * `device::Device`
  * `create_info::_CommandPoolCreateInfo`
  * `allocator::_AllocationCallbacks`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateCommandPool.html)

```julia
_create_command_pool(
    device,
    create_info::Vulkan._CommandPoolCreateInfo;
    allocator
) -> ResultTypes.Result{Vulkan.CommandPool, Vulkan.VulkanError}

```
