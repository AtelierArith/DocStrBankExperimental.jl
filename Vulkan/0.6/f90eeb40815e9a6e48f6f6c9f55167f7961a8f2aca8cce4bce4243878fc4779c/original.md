High-level wrapper for VkCopyAccelerationStructureToMemoryInfoKHR.

Extension: VK_KHR_acceleration_structure

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCopyAccelerationStructureToMemoryInfoKHR.html)

```julia
struct CopyAccelerationStructureToMemoryInfoKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `src::Vulkan.AccelerationStructureKHR`
  * `dst::Vulkan.DeviceOrHostAddressKHR`
  * `mode::Vulkan.CopyAccelerationStructureModeKHR`
