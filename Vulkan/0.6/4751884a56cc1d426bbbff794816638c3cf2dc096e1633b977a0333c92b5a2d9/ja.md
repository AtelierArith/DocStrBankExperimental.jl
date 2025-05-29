引数:

  * `robust_image_access::Bool`
  * `inline_uniform_block::Bool`
  * `descriptor_binding_inline_uniform_block_update_after_bind::Bool`
  * `pipeline_creation_cache_control::Bool`
  * `private_data::Bool`
  * `shader_demote_to_helper_invocation::Bool`
  * `shader_terminate_invocation::Bool`
  * `subgroup_size_control::Bool`
  * `compute_full_subgroups::Bool`
  * `synchronization2::Bool`
  * `texture_compression_astc_hdr::Bool`
  * `shader_zero_initialize_workgroup_memory::Bool`
  * `dynamic_rendering::Bool`
  * `shader_integer_dot_product::Bool`
  * `maintenance4::Bool`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceVulkan13Features.html)

```julia
PhysicalDeviceVulkan13Features(
    robust_image_access::Bool,
    inline_uniform_block::Bool,
    descriptor_binding_inline_uniform_block_update_after_bind::Bool,
    pipeline_creation_cache_control::Bool,
    private_data::Bool,
    shader_demote_to_helper_invocation::Bool,
    shader_terminate_invocation::Bool,
    subgroup_size_control::Bool,
    compute_full_subgroups::Bool,
    synchronization2::Bool,
    texture_compression_astc_hdr::Bool,
    shader_zero_initialize_workgroup_memory::Bool,
    dynamic_rendering::Bool,
    shader_integer_dot_product::Bool,
    maintenance4::Bool;
    next
) -> Vulkan.PhysicalDeviceVulkan13Features

```
