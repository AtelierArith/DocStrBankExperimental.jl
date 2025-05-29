拡張: VK*EXT*primitive*topology*list_restart

引数:

  * `primitive_topology_list_restart::Bool`
  * `primitive_topology_patch_list_restart::Bool`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDevicePrimitiveTopologyListRestartFeaturesEXT.html)

```julia
_PhysicalDevicePrimitiveTopologyListRestartFeaturesEXT(
    primitive_topology_list_restart::Bool,
    primitive_topology_patch_list_restart::Bool;
    next
) -> Vulkan._PhysicalDevicePrimitiveTopologyListRestartFeaturesEXT

```
