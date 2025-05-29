VkGeometryTrianglesNVの高レベルラッパー。

拡張: VK*NV*ray_tracing

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkGeometryTrianglesNV.html)

```julia
struct GeometryTrianglesNV <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `vertex_data::Union{Ptr{Nothing}, Vulkan.Buffer}`
  * `vertex_offset::UInt64`
  * `vertex_count::UInt32`
  * `vertex_stride::UInt64`
  * `vertex_format::Vulkan.Format`
  * `index_data::Union{Ptr{Nothing}, Vulkan.Buffer}`
  * `index_offset::UInt64`
  * `index_count::UInt32`
  * `index_type::Vulkan.IndexType`
  * `transform_data::Union{Ptr{Nothing}, Vulkan.Buffer}`
  * `transform_offset::UInt64`
