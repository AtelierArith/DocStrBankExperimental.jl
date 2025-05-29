拡張: VK*KHR*acceleration_structure

引数:

  * `buffer::Buffer`
  * `offset::UInt64`
  * `size::UInt64`
  * `type::AccelerationStructureTypeKHR`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `create_flags::AccelerationStructureCreateFlagKHR`: デフォルトは `0`
  * `device_address::UInt64`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAccelerationStructureCreateInfoKHR.html)

```julia
_AccelerationStructureCreateInfoKHR(
    buffer,
    offset::Integer,
    size::Integer,
    type::Vulkan.AccelerationStructureTypeKHR;
    next,
    create_flags,
    device_address
) -> Vulkan._AccelerationStructureCreateInfoKHR

```
