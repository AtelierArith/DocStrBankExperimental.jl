Extension: VK_KHR_acceleration_structure

Arguments:

  * `src::AccelerationStructureKHR`
  * `dst::DeviceOrHostAddressKHR`
  * `mode::CopyAccelerationStructureModeKHR`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCopyAccelerationStructureToMemoryInfoKHR.html)

```julia
CopyAccelerationStructureToMemoryInfoKHR(
    src::Vulkan.AccelerationStructureKHR,
    dst::Vulkan.DeviceOrHostAddressKHR,
    mode::Vulkan.CopyAccelerationStructureModeKHR;
    next
) -> Vulkan.CopyAccelerationStructureToMemoryInfoKHR

```
