拡張: VK*KHR*acceleration_structure

引数:

  * `buffer::Buffer`
  * `offset::UInt64`
  * `size::UInt64`
  * `type::AccelerationStructureTypeKHR`
  * `next::Any`: デフォルトは `C_NULL`
  * `create_flags::AccelerationStructureCreateFlagKHR`: デフォルトは `0`
  * `device_address::UInt64`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAccelerationStructureCreateInfoKHR.html)

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
