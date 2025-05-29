Arguments:

  * `subgroup_size::UInt32`
  * `supported_stages::ShaderStageFlag`
  * `supported_operations::SubgroupFeatureFlag`
  * `quad_operations_in_all_stages::Bool`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceSubgroupProperties.html)

```julia
PhysicalDeviceSubgroupProperties(
    subgroup_size::Integer,
    supported_stages::Vulkan.ShaderStageFlag,
    supported_operations::Vulkan.SubgroupFeatureFlag,
    quad_operations_in_all_stages::Bool;
    next
) -> Vulkan.PhysicalDeviceSubgroupProperties

```
