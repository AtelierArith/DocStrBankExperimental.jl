戻り値:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

引数:

  * `device::Device`
  * `create_info::CommandPoolCreateInfo`
  * `allocator::AllocationCallbacks`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateCommandPool.html)

```julia
create_command_pool(
    device,
    create_info::Vulkan.CommandPoolCreateInfo;
    allocator
) -> ResultTypes.Result{Vulkan.CommandPool, Vulkan.VulkanError}

```
