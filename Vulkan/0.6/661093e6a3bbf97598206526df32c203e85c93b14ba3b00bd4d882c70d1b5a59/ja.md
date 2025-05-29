拡張: VK*KHR*acceleration_structure

戻りコード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_INVALID_OPAQUE_CAPTURE_ADDRESS_KHR`

引数:

  * `device::Device`
  * `buffer::Buffer`
  * `offset::UInt64`
  * `size::UInt64`
  * `type::AccelerationStructureTypeKHR`
  * `allocator::_AllocationCallbacks`: デフォルトは `C_NULL`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `create_flags::AccelerationStructureCreateFlagKHR`: デフォルトは `0`
  * `device_address::UInt64`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateAccelerationStructureKHR.html)

```julia
_create_acceleration_structure_khr(
    device,
    buffer,
    offset::Integer,
    size::Integer,
    type::Vulkan.AccelerationStructureTypeKHR;
    allocator,
    next,
    create_flags,
    device_address
) -> ResultTypes.Result{Vulkan.AccelerationStructureKHR, Vulkan.VulkanError}

```
