拡張: VK*KHR*acceleration_structure

引数:

  * `src::_DeviceOrHostAddressConstKHR`
  * `dst::AccelerationStructureKHR`
  * `mode::CopyAccelerationStructureModeKHR`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCopyMemoryToAccelerationStructureInfoKHR.html)

```julia
_CopyMemoryToAccelerationStructureInfoKHR(
    src::Vulkan._DeviceOrHostAddressConstKHR,
    dst,
    mode::Vulkan.CopyAccelerationStructureModeKHR;
    next
) -> Vulkan._CopyMemoryToAccelerationStructureInfoKHR

```
