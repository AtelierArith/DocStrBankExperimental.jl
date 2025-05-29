Intermediate wrapper for VkGeometryAABBNV.

Extension: VK_NV_ray_tracing

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkGeometryAABBNV.html)

```julia
struct _GeometryAABBNV <: Vulkan.VulkanStruct{true}
```

  * `vks::VulkanCore.LibVulkan.VkGeometryAABBNV`
  * `deps::Vector{Any}`
  * `aabb_data::Union{Ptr{Nothing}, Vulkan.Buffer}`
