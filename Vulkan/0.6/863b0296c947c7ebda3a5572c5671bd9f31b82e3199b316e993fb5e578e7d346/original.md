Extension: VK_KHR_acceleration_structure

Arguments:

  * `buffer::Buffer`
  * `offset::UInt64`
  * `size::UInt64`
  * `type::AccelerationStructureTypeKHR`
  * `next::Any`: defaults to `C_NULL`
  * `create_flags::AccelerationStructureCreateFlagKHR`: defaults to `0`
  * `device_address::UInt64`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAccelerationStructureCreateInfoKHR.html)

```julia
AccelerationStructureCreateInfoKHR(
    buffer::Vulkan.Buffer,
    offset::Integer,
    size::Integer,
    type::Vulkan.AccelerationStructureTypeKHR;
    next,
    create_flags,
    device_address
) -> Vulkan.AccelerationStructureCreateInfoKHR

```
