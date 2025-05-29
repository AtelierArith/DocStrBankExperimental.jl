拡張: VK*KHR*acceleration_structure

引数:

  * `src::DeviceOrHostAddressConstKHR`
  * `dst::AccelerationStructureKHR`
  * `mode::CopyAccelerationStructureModeKHR`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCopyMemoryToAccelerationStructureInfoKHR.html)

```julia
CopyMemoryToAccelerationStructureInfoKHR(
    src::Vulkan.DeviceOrHostAddressConstKHR,
    dst::Vulkan.AccelerationStructureKHR,
    mode::Vulkan.CopyAccelerationStructureModeKHR;
    next
) -> Vulkan.CopyMemoryToAccelerationStructureInfoKHR

```
