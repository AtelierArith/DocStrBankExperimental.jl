Extension: VK_EXT_provoking_vertex

Arguments:

  * `provoking_vertex_mode_per_pipeline::Bool`
  * `transform_feedback_preserves_triangle_fan_provoking_vertex::Bool`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceProvokingVertexPropertiesEXT.html)

```julia
_PhysicalDeviceProvokingVertexPropertiesEXT(
    provoking_vertex_mode_per_pipeline::Bool,
    transform_feedback_preserves_triangle_fan_provoking_vertex::Bool;
    next
) -> Vulkan._PhysicalDeviceProvokingVertexPropertiesEXT

```
