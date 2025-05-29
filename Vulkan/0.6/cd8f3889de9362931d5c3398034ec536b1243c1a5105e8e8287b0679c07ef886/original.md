Extension: VK_KHR_acceleration_structure

Arguments:

  * `data::_DeviceOrHostAddressConstKHR`
  * `stride::UInt64`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAccelerationStructureGeometryAabbsDataKHR.html)

```julia
_AccelerationStructureGeometryAabbsDataKHR(
    data::Vulkan._DeviceOrHostAddressConstKHR,
    stride::Integer;
    next
) -> Vulkan._AccelerationStructureGeometryAabbsDataKHR

```
