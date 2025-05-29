返すコード：

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

引数：

  * `device::Device`
  * `create_info::_EventCreateInfo`
  * `allocator::_AllocationCallbacks`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateEvent.html)

```julia
_create_event(
    device,
    create_info::Vulkan._EventCreateInfo;
    allocator
) -> ResultTypes.Result{Vulkan.Event, Vulkan.VulkanError}

```
