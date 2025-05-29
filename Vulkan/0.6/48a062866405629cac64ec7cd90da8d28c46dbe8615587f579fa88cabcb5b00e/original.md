Extension: VK_KHR_acceleration_structure

Arguments:

  * `array_of_pointers::Bool`
  * `data::_DeviceOrHostAddressConstKHR`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAccelerationStructureGeometryInstancesDataKHR.html)

```julia
_AccelerationStructureGeometryInstancesDataKHR(
    array_of_pointers::Bool,
    data::Vulkan._DeviceOrHostAddressConstKHR;
    next
) -> Vulkan._AccelerationStructureGeometryInstancesDataKHR

```
