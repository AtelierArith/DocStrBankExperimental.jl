Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

Arguments:

  * `device::Device`
  * `queue_family_index::UInt32`
  * `allocator::_AllocationCallbacks`: defaults to `C_NULL`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `flags::CommandPoolCreateFlag`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateCommandPool.html)

```julia
_create_command_pool(
    device,
    queue_family_index::Integer;
    allocator,
    next,
    flags
) -> ResultTypes.Result{Vulkan.CommandPool, Vulkan.VulkanError}

```
