拡張: VK*KHR*acceleration_structure

引数:

  * `array_of_pointers::Bool`
  * `data::DeviceOrHostAddressConstKHR`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAccelerationStructureGeometryInstancesDataKHR.html)

```julia
AccelerationStructureGeometryInstancesDataKHR(
    array_of_pointers::Bool,
    data::Vulkan.DeviceOrHostAddressConstKHR;
    next
) -> Vulkan.AccelerationStructureGeometryInstancesDataKHR

```
