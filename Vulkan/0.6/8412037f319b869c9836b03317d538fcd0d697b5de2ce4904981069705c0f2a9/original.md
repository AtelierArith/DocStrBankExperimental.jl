Extension: VK_HUAWEI_cluster_culling_shader

Arguments:

  * `clusterculling_shader::Bool`
  * `multiview_cluster_culling_shader::Bool`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceClusterCullingShaderFeaturesHUAWEI.html)

```julia
_PhysicalDeviceClusterCullingShaderFeaturesHUAWEI(
    clusterculling_shader::Bool,
    multiview_cluster_culling_shader::Bool;
    next
) -> Vulkan._PhysicalDeviceClusterCullingShaderFeaturesHUAWEI

```
