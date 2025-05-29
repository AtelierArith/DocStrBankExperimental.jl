High-level wrapper for VkGeometryAABBNV.

Extension: VK_NV_ray_tracing

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkGeometryAABBNV.html)

```julia
struct GeometryAABBNV <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `aabb_data::Union{Ptr{Nothing}, Vulkan.Buffer}`
  * `num_aab_bs::UInt32`
  * `stride::UInt32`
  * `offset::UInt64`
