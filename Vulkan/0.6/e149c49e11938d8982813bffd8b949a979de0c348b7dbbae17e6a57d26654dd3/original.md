High-level wrapper for VkAccelerationStructureBuildRangeInfoKHR.

Extension: VK_KHR_acceleration_structure

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAccelerationStructureBuildRangeInfoKHR.html)

```julia
struct AccelerationStructureBuildRangeInfoKHR <: Vulkan.HighLevelStruct
```

  * `primitive_count::UInt32`
  * `primitive_offset::UInt32`
  * `first_vertex::UInt32`
  * `transform_offset::UInt32`
