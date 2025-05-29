High-level wrapper for VkAccelerationStructureGeometryTrianglesDataKHR.

Extension: VK_KHR_acceleration_structure

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAccelerationStructureGeometryTrianglesDataKHR.html)

```julia
struct AccelerationStructureGeometryTrianglesDataKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `vertex_format::Vulkan.Format`
  * `vertex_data::Vulkan.DeviceOrHostAddressConstKHR`
  * `vertex_stride::UInt64`
  * `max_vertex::UInt32`
  * `index_type::Vulkan.IndexType`
  * `index_data::Vulkan.DeviceOrHostAddressConstKHR`
  * `transform_data::Vulkan.DeviceOrHostAddressConstKHR`
