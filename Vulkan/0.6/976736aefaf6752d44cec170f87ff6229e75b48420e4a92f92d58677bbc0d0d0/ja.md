拡張: VK*EXT*display_control

戻りコード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`

引数:

  * `device::Device`
  * `device_event_info::_DeviceEventInfoEXT`
  * `allocator::_AllocationCallbacks`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkRegisterDeviceEventEXT.html)

```julia
_register_device_event_ext(
    device,
    device_event_info::Vulkan._DeviceEventInfoEXT;
    allocator
) -> ResultTypes.Result{Vulkan.Fence, Vulkan.VulkanError}

```
