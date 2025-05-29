Extension: VK_HUAWEI_cluster_culling_shader

Arguments:

  * `max_work_group_count::NTuple{3, UInt32}`
  * `max_work_group_size::NTuple{3, UInt32}`
  * `max_output_cluster_count::UInt32`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceClusterCullingShaderPropertiesHUAWEI.html)

```julia
_PhysicalDeviceClusterCullingShaderPropertiesHUAWEI(
    max_work_group_count::Tuple{UInt32, UInt32, UInt32},
    max_work_group_size::Tuple{UInt32, UInt32, UInt32},
    max_output_cluster_count::Integer;
    next
) -> Vulkan._PhysicalDeviceClusterCullingShaderPropertiesHUAWEI

```
