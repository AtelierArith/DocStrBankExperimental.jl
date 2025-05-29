Arguments:

  * `min_subgroup_size::UInt32`
  * `max_subgroup_size::UInt32`
  * `max_compute_workgroup_subgroups::UInt32`
  * `required_subgroup_size_stages::ShaderStageFlag`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceSubgroupSizeControlProperties.html)

```julia
PhysicalDeviceSubgroupSizeControlProperties(
    min_subgroup_size::Integer,
    max_subgroup_size::Integer,
    max_compute_workgroup_subgroups::Integer,
    required_subgroup_size_stages::Vulkan.ShaderStageFlag;
    next
) -> Vulkan.PhysicalDeviceSubgroupSizeControlProperties

```
