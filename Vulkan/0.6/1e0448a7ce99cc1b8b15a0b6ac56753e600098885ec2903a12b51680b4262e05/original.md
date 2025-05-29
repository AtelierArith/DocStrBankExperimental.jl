High-level wrapper for VkCopyMemoryToAccelerationStructureInfoKHR.

Extension: VK_KHR_acceleration_structure

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCopyMemoryToAccelerationStructureInfoKHR.html)

```julia
struct CopyMemoryToAccelerationStructureInfoKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `src::Vulkan.DeviceOrHostAddressConstKHR`
  * `dst::Vulkan.AccelerationStructureKHR`
  * `mode::Vulkan.CopyAccelerationStructureModeKHR`
