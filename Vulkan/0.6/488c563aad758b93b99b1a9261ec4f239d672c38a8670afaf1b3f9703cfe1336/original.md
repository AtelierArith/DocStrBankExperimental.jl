High-level wrapper for VkAccelerationStructureGeometryKHR.

Extension: VK_KHR_acceleration_structure

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAccelerationStructureGeometryKHR.html)

```julia
struct AccelerationStructureGeometryKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `geometry_type::Vulkan.GeometryTypeKHR`
  * `geometry::Vulkan.AccelerationStructureGeometryDataKHR`
  * `flags::Vulkan.GeometryFlagKHR`
