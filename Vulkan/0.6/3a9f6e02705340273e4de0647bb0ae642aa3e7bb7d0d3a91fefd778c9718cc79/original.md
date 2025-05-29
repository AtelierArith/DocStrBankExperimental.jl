Extension: VK_KHR_acceleration_structure

Arguments:

  * `src::AccelerationStructureKHR`
  * `dst::_DeviceOrHostAddressKHR`
  * `mode::CopyAccelerationStructureModeKHR`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCopyAccelerationStructureToMemoryInfoKHR.html)

```julia
_CopyAccelerationStructureToMemoryInfoKHR(
    src,
    dst::Vulkan._DeviceOrHostAddressKHR,
    mode::Vulkan.CopyAccelerationStructureModeKHR;
    next
) -> Vulkan._CopyAccelerationStructureToMemoryInfoKHR

```
