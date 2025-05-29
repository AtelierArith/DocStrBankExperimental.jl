Extension: VK_KHR_acceleration_structure

Arguments:

  * `src::AccelerationStructureKHR`
  * `dst::AccelerationStructureKHR`
  * `mode::CopyAccelerationStructureModeKHR`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCopyAccelerationStructureInfoKHR.html)

```julia
_CopyAccelerationStructureInfoKHR(
    src,
    dst,
    mode::Vulkan.CopyAccelerationStructureModeKHR;
    next
) -> Vulkan._CopyAccelerationStructureInfoKHR

```
