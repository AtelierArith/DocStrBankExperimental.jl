Extension: VK_KHR_acceleration_structure

Arguments:

  * `array_of_pointers::Bool`
  * `data::DeviceOrHostAddressConstKHR`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAccelerationStructureGeometryInstancesDataKHR.html)

```julia
AccelerationStructureGeometryInstancesDataKHR(
    array_of_pointers::Bool,
    data::Vulkan.DeviceOrHostAddressConstKHR;
    next
) -> Vulkan.AccelerationStructureGeometryInstancesDataKHR

```
