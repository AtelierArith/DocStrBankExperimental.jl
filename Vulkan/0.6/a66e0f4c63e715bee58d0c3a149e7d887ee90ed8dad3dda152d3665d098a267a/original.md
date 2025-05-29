Extension: VK_EXT_primitive_topology_list_restart

Arguments:

  * `primitive_topology_list_restart::Bool`
  * `primitive_topology_patch_list_restart::Bool`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDevicePrimitiveTopologyListRestartFeaturesEXT.html)

```julia
_PhysicalDevicePrimitiveTopologyListRestartFeaturesEXT(
    primitive_topology_list_restart::Bool,
    primitive_topology_patch_list_restart::Bool;
    next
) -> Vulkan._PhysicalDevicePrimitiveTopologyListRestartFeaturesEXT

```
