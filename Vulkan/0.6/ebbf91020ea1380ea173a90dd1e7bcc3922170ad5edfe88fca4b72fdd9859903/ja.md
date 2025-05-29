拡張: VK*KHR*acceleration_structure

引数:

  * `src::AccelerationStructureKHR`
  * `dst::DeviceOrHostAddressKHR`
  * `mode::CopyAccelerationStructureModeKHR`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCopyAccelerationStructureToMemoryInfoKHR.html)

```julia
CopyAccelerationStructureToMemoryInfoKHR(
    src::Vulkan.AccelerationStructureKHR,
    dst::Vulkan.DeviceOrHostAddressKHR,
    mode::Vulkan.CopyAccelerationStructureModeKHR;
    next
) -> Vulkan.CopyAccelerationStructureToMemoryInfoKHR

```
