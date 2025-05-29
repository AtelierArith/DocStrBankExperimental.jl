Extension: VK_KHR_acceleration_structure

Arguments:

  * `device::Device`
  * `buffer::Buffer`
  * `offset::UInt64`
  * `size::UInt64`
  * `type::AccelerationStructureTypeKHR`
  * `allocator::AllocationCallbacks`: defaults to `C_NULL`
  * `next::Any`: defaults to `C_NULL`
  * `create_flags::AccelerationStructureCreateFlagKHR`: defaults to `0`
  * `device_address::UInt64`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateAccelerationStructureKHR.html)

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
