Extension: VK_NV_mesh_shader

Arguments:

  * `task_shader::Bool`
  * `mesh_shader::Bool`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceMeshShaderFeaturesNV.html)

```julia
_PhysicalDeviceMeshShaderFeaturesNV(
    task_shader::Bool,
    mesh_shader::Bool;
    next
) -> Vulkan._PhysicalDeviceMeshShaderFeaturesNV

```
