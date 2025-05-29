High-level wrapper for VkAccelerationStructureBuildSizesInfoKHR.

Extension: VK_KHR_acceleration_structure

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAccelerationStructureBuildSizesInfoKHR.html)

```julia
struct AccelerationStructureBuildSizesInfoKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `acceleration_structure_size::UInt64`
  * `update_scratch_size::UInt64`
  * `build_scratch_size::UInt64`
