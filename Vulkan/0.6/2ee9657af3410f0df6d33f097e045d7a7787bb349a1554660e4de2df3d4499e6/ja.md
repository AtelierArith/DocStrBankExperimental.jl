VkPhysicalDeviceSubgroupPropertiesの高レベルラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceSubgroupProperties.html)

```julia
struct PhysicalDeviceSubgroupProperties <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `subgroup_size::UInt32`
  * `supported_stages::Vulkan.ShaderStageFlag`
  * `supported_operations::Vulkan.SubgroupFeatureFlag`
  * `quad_operations_in_all_stages::Bool`
