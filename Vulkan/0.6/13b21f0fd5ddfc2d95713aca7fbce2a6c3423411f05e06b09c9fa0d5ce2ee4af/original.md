Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`
  * `ERROR_INITIALIZATION_FAILED`
  * `ERROR_EXTENSION_NOT_PRESENT`
  * `ERROR_FEATURE_NOT_PRESENT`
  * `ERROR_TOO_MANY_OBJECTS`
  * `ERROR_DEVICE_LOST`

Arguments:

  * `physical_device::PhysicalDevice`
  * `create_info::_DeviceCreateInfo`
  * `allocator::_AllocationCallbacks`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateDevice.html)

```julia
_create_device(
    physical_device,
    create_info::Vulkan._DeviceCreateInfo;
    allocator
) -> ResultTypes.Result{Vulkan.Device, Vulkan.VulkanError}

```
