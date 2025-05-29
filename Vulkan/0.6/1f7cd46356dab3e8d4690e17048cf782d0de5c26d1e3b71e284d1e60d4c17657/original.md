High-level wrapper for VkPhysicalDeviceClusterCullingShaderPropertiesHUAWEI.

Extension: VK_HUAWEI_cluster_culling_shader

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceClusterCullingShaderPropertiesHUAWEI.html)

```julia
struct PhysicalDeviceClusterCullingShaderPropertiesHUAWEI <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `max_work_group_count::Tuple{UInt32, UInt32, UInt32}`
  * `max_work_group_size::Tuple{UInt32, UInt32, UInt32}`
  * `max_output_cluster_count::UInt32`
