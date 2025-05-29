Arguments:

  * `device_uuid::NTuple{Int(VK_UUID_SIZE), UInt8}`
  * `driver_uuid::NTuple{Int(VK_UUID_SIZE), UInt8}`
  * `device_luid::NTuple{Int(VK_LUID_SIZE), UInt8}`
  * `device_node_mask::UInt32`
  * `device_luid_valid::Bool`
  * `subgroup_size::UInt32`
  * `subgroup_supported_stages::ShaderStageFlag`
  * `subgroup_supported_operations::SubgroupFeatureFlag`
  * `subgroup_quad_operations_in_all_stages::Bool`
  * `point_clipping_behavior::PointClippingBehavior`
  * `max_multiview_view_count::UInt32`
  * `max_multiview_instance_index::UInt32`
  * `protected_no_fault::Bool`
  * `max_per_set_descriptors::UInt32`
  * `max_memory_allocation_size::UInt64`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceVulkan11Properties.html)

```julia
_PhysicalDeviceVulkan11Properties(
    device_uuid::NTuple{16, UInt8},
    driver_uuid::NTuple{16, UInt8},
    device_luid::NTuple{8, UInt8},
    device_node_mask::Integer,
    device_luid_valid::Bool,
    subgroup_size::Integer,
    subgroup_supported_stages::Vulkan.ShaderStageFlag,
    subgroup_supported_operations::Vulkan.SubgroupFeatureFlag,
    subgroup_quad_operations_in_all_stages::Bool,
    point_clipping_behavior::Vulkan.PointClippingBehavior,
    max_multiview_view_count::Integer,
    max_multiview_instance_index::Integer,
    protected_no_fault::Bool,
    max_per_set_descriptors::Integer,
    max_memory_allocation_size::Integer;
    next
) -> Vulkan._PhysicalDeviceVulkan11Properties

```
