拡張: VK*KHR*acceleration_structure

引数:

  * `device::Device`
  * `buffer::Buffer`
  * `offset::UInt64`
  * `size::UInt64`
  * `type::AccelerationStructureTypeKHR`
  * `allocator::AllocationCallbacks`: デフォルトは `C_NULL`
  * `next::Any`: デフォルトは `C_NULL`
  * `create_flags::AccelerationStructureCreateFlagKHR`: デフォルトは `0`
  * `device_address::UInt64`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateAccelerationStructureKHR.html)

```julia
AccelerationStructureKHR(
    device,
    buffer,
    offset::Integer,
    size::Integer,
    type::Vulkan.AccelerationStructureTypeKHR;
    allocator,
    next,
    create_flags,
    device_address
) -> Vulkan.AccelerationStructureKHR

```
