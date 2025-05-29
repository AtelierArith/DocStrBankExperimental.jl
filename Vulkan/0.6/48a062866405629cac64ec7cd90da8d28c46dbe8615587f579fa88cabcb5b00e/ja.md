拡張: VK*KHR*acceleration_structure

引数:

  * `array_of_pointers::Bool`
  * `data::_DeviceOrHostAddressConstKHR`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAccelerationStructureGeometryInstancesDataKHR.html)

```julia
_AccelerationStructureGeometryInstancesDataKHR(
    array_of_pointers::Bool,
    data::Vulkan._DeviceOrHostAddressConstKHR;
    next
) -> Vulkan._AccelerationStructureGeometryInstancesDataKHR

```
