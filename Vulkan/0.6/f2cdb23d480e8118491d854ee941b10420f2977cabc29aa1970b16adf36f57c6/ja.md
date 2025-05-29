拡張: VK*HUAWEI*cluster*culling*shader

引数:

  * `max_work_group_count::NTuple{3, UInt32}`
  * `max_work_group_size::NTuple{3, UInt32}`
  * `max_output_cluster_count::UInt32`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceClusterCullingShaderPropertiesHUAWEI.html)

```julia
PhysicalDeviceClusterCullingShaderPropertiesHUAWEI(
    max_work_group_count::Tuple{UInt32, UInt32, UInt32},
    max_work_group_size::Tuple{UInt32, UInt32, UInt32},
    max_output_cluster_count::Integer;
    next
) -> Vulkan.PhysicalDeviceClusterCullingShaderPropertiesHUAWEI

```
