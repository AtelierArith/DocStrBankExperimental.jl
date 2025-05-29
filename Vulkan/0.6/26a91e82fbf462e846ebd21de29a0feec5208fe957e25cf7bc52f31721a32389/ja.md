拡張: VK*KHR*acceleration_structure

引数:

  * `data::DeviceOrHostAddressConstKHR`
  * `stride::UInt64`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAccelerationStructureGeometryAabbsDataKHR.html)

```julia
AccelerationStructureGeometryAabbsDataKHR(
    data::Vulkan.DeviceOrHostAddressConstKHR,
    stride::Integer;
    next
) -> Vulkan.AccelerationStructureGeometryAabbsDataKHR

```
