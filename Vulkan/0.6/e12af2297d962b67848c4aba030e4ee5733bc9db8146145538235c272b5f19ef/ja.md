拡張: VK*KHR*acceleration_structure

戻りコード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_INVALID_OPAQUE_CAPTURE_ADDRESS_KHR`

引数:

  * `device::Device`
  * `create_info::AccelerationStructureCreateInfoKHR`
  * `allocator::AllocationCallbacks`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateAccelerationStructureKHR.html)

```julia
create_acceleration_structure_khr(
    device,
    create_info::Vulkan.AccelerationStructureCreateInfoKHR;
    allocator
) -> ResultTypes.Result{Vulkan.AccelerationStructureKHR, Vulkan.VulkanError}

```
