Extension: VK_NV_ray_tracing

Arguments:

  * `vertex_offset::UInt64`
  * `vertex_count::UInt32`
  * `vertex_stride::UInt64`
  * `vertex_format::Format`
  * `index_offset::UInt64`
  * `index_count::UInt32`
  * `index_type::IndexType`
  * `transform_offset::UInt64`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `vertex_data::Buffer`: defaults to `C_NULL`
  * `index_data::Buffer`: defaults to `C_NULL`
  * `transform_data::Buffer`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkGeometryTrianglesNV.html)

```julia
_GeometryTrianglesNV(
    vertex_offset::Integer,
    vertex_count::Integer,
    vertex_stride::Integer,
    vertex_format::Vulkan.Format,
    index_offset::Integer,
    index_count::Integer,
    index_type::Vulkan.IndexType,
    transform_offset::Integer;
    next,
    vertex_data,
    index_data,
    transform_data
) -> Vulkan._GeometryTrianglesNV

```
