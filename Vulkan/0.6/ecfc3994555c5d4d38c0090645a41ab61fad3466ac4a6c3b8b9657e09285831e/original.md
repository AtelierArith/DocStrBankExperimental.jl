High-level wrapper for VkCopyAccelerationStructureInfoKHR.

Extension: VK_KHR_acceleration_structure

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCopyAccelerationStructureInfoKHR.html)

```julia
struct CopyAccelerationStructureInfoKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `src::Vulkan.AccelerationStructureKHR`
  * `dst::Vulkan.AccelerationStructureKHR`
  * `mode::Vulkan.CopyAccelerationStructureModeKHR`
