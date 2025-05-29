Extension: VK_KHR_acceleration_structure

Arguments:

  * `data::DeviceOrHostAddressConstKHR`
  * `stride::UInt64`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAccelerationStructureGeometryAabbsDataKHR.html)

```julia
AccelerationStructureGeometryAabbsDataKHR(
    data::Vulkan.DeviceOrHostAddressConstKHR,
    stride::Integer;
    next
) -> Vulkan.AccelerationStructureGeometryAabbsDataKHR

```
