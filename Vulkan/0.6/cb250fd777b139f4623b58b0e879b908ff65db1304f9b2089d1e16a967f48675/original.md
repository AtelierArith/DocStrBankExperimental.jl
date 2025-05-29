Extension: VK_KHR_acceleration_structure

Arguments:

  * `src::DeviceOrHostAddressConstKHR`
  * `dst::AccelerationStructureKHR`
  * `mode::CopyAccelerationStructureModeKHR`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCopyMemoryToAccelerationStructureInfoKHR.html)

```julia
CopyMemoryToAccelerationStructureInfoKHR(
    src::Vulkan.DeviceOrHostAddressConstKHR,
    dst::Vulkan.AccelerationStructureKHR,
    mode::Vulkan.CopyAccelerationStructureModeKHR;
    next
) -> Vulkan.CopyMemoryToAccelerationStructureInfoKHR

```
