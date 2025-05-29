Extension: VK_KHR_acceleration_structure

Arguments:

  * `src::AccelerationStructureKHR`
  * `dst::AccelerationStructureKHR`
  * `mode::CopyAccelerationStructureModeKHR`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCopyAccelerationStructureInfoKHR.html)

```julia
CopyAccelerationStructureInfoKHR(
    src::Vulkan.AccelerationStructureKHR,
    dst::Vulkan.AccelerationStructureKHR,
    mode::Vulkan.CopyAccelerationStructureModeKHR;
    next
) -> Vulkan.CopyAccelerationStructureInfoKHR

```
