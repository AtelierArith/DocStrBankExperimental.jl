拡張: VK*KHR*acceleration_structure

引数:

  * `src::AccelerationStructureKHR`
  * `dst::_DeviceOrHostAddressKHR`
  * `mode::CopyAccelerationStructureModeKHR`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCopyAccelerationStructureToMemoryInfoKHR.html)

```julia
_CopyAccelerationStructureToMemoryInfoKHR(
    src,
    dst::Vulkan._DeviceOrHostAddressKHR,
    mode::Vulkan.CopyAccelerationStructureModeKHR;
    next
) -> Vulkan._CopyAccelerationStructureToMemoryInfoKHR

```
