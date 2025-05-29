Extension: VK_KHR_acceleration_structure

Arguments:

  * `src::_DeviceOrHostAddressConstKHR`
  * `dst::AccelerationStructureKHR`
  * `mode::CopyAccelerationStructureModeKHR`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCopyMemoryToAccelerationStructureInfoKHR.html)

```julia
_CopyMemoryToAccelerationStructureInfoKHR(
    src::Vulkan._DeviceOrHostAddressConstKHR,
    dst,
    mode::Vulkan.CopyAccelerationStructureModeKHR;
    next
) -> Vulkan._CopyMemoryToAccelerationStructureInfoKHR

```
