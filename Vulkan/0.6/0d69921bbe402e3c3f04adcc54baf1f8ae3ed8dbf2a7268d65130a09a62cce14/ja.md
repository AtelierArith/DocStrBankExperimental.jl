戻り値:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

引数:

  * `device::Device`
  * `queue_family_index::UInt32`
  * `allocator::_AllocationCallbacks`: デフォルトは `C_NULL`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `flags::CommandPoolCreateFlag`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateCommandPool.html)

```julia
_create_command_pool(
    device,
    queue_family_index::Integer;
    allocator,
    next,
    flags
) -> ResultTypes.Result{Vulkan.CommandPool, Vulkan.VulkanError}

```
