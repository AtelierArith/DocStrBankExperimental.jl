High-level wrapper for VkGeometryNV.

Extension: VK_NV_ray_tracing

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkGeometryNV.html)

```julia
struct GeometryNV <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `geometry_type::Vulkan.GeometryTypeKHR`
  * `geometry::Vulkan.GeometryDataNV`
  * `flags::Vulkan.GeometryFlagKHR`
