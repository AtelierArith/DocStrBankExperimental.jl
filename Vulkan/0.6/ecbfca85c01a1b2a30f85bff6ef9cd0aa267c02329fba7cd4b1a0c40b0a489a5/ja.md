拡張: VK*KHR*acceleration_structure

引数:

  * `src::AccelerationStructureKHR`
  * `dst::AccelerationStructureKHR`
  * `mode::CopyAccelerationStructureModeKHR`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCopyAccelerationStructureInfoKHR.html)

```julia
_CopyAccelerationStructureInfoKHR(
    src,
    dst,
    mode::Vulkan.CopyAccelerationStructureModeKHR;
    next
) -> Vulkan._CopyAccelerationStructureInfoKHR

```
