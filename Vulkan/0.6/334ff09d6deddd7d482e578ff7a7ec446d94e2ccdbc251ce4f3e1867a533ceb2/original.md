Extension: VK_EXT_mesh_shader

Arguments:

  * `task_shader::Bool`
  * `mesh_shader::Bool`
  * `multiview_mesh_shader::Bool`
  * `primitive_fragment_shading_rate_mesh_shader::Bool`
  * `mesh_shader_queries::Bool`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceMeshShaderFeaturesEXT.html)

```julia
_PhysicalDeviceMeshShaderFeaturesEXT(
    task_shader::Bool,
    mesh_shader::Bool,
    multiview_mesh_shader::Bool,
    primitive_fragment_shading_rate_mesh_shader::Bool,
    mesh_shader_queries::Bool;
    next
) -> Vulkan._PhysicalDeviceMeshShaderFeaturesEXT

```
