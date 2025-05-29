Extension: VK_KHR_acceleration_structure

Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_INVALID_OPAQUE_CAPTURE_ADDRESS_KHR`

Arguments:

  * `device::Device`
  * `create_info::_AccelerationStructureCreateInfoKHR`
  * `allocator::_AllocationCallbacks`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateAccelerationStructureKHR.html)

```julia
_create_acceleration_structure_khr(
    device,
    create_info::Vulkan._AccelerationStructureCreateInfoKHR;
    allocator
) -> ResultTypes.Result{Vulkan.AccelerationStructureKHR, Vulkan.VulkanError}

```
