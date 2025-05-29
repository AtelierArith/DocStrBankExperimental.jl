拡張: VK*KHR*acceleration_structure

引数:

  * `data::_DeviceOrHostAddressConstKHR`
  * `stride::UInt64`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAccelerationStructureGeometryAabbsDataKHR.html)

```julia
_AccelerationStructureGeometryAabbsDataKHR(
    data::Vulkan._DeviceOrHostAddressConstKHR,
    stride::Integer;
    next
) -> Vulkan._AccelerationStructureGeometryAabbsDataKHR

```
