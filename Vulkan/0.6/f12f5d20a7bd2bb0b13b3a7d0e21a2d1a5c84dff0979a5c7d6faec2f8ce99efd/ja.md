拡張: VK*EXT*provoking_vertex

引数:

  * `provoking_vertex_mode_per_pipeline::Bool`
  * `transform_feedback_preserves_triangle_fan_provoking_vertex::Bool`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceProvokingVertexPropertiesEXT.html)

```julia
_PhysicalDeviceProvokingVertexPropertiesEXT(
    provoking_vertex_mode_per_pipeline::Bool,
    transform_feedback_preserves_triangle_fan_provoking_vertex::Bool;
    next
) -> Vulkan._PhysicalDeviceProvokingVertexPropertiesEXT

```
