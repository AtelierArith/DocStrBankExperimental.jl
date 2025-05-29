中間ラッパー VkGeometryTrianglesNV。

拡張: VK*NV*ray_tracing

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkGeometryTrianglesNV.html)

```julia
struct _GeometryTrianglesNV <: Vulkan.VulkanStruct{true}
```

  * `vks::VulkanCore.LibVulkan.VkGeometryTrianglesNV`
  * `deps::Vector{Any}`
  * `vertex_data::Union{Ptr{Nothing}, Vulkan.Buffer}`
  * `index_data::Union{Ptr{Nothing}, Vulkan.Buffer}`
  * `transform_data::Union{Ptr{Nothing}, Vulkan.Buffer}`
