Arguments:

  * `sampler_mirror_clamp_to_edge::Bool`
  * `draw_indirect_count::Bool`
  * `storage_buffer_8_bit_access::Bool`
  * `uniform_and_storage_buffer_8_bit_access::Bool`
  * `storage_push_constant_8::Bool`
  * `shader_buffer_int_64_atomics::Bool`
  * `shader_shared_int_64_atomics::Bool`
  * `shader_float_16::Bool`
  * `shader_int_8::Bool`
  * `descriptor_indexing::Bool`
  * `shader_input_attachment_array_dynamic_indexing::Bool`
  * `shader_uniform_texel_buffer_array_dynamic_indexing::Bool`
  * `shader_storage_texel_buffer_array_dynamic_indexing::Bool`
  * `shader_uniform_buffer_array_non_uniform_indexing::Bool`
  * `shader_sampled_image_array_non_uniform_indexing::Bool`
  * `shader_storage_buffer_array_non_uniform_indexing::Bool`
  * `shader_storage_image_array_non_uniform_indexing::Bool`
  * `shader_input_attachment_array_non_uniform_indexing::Bool`
  * `shader_uniform_texel_buffer_array_non_uniform_indexing::Bool`
  * `shader_storage_texel_buffer_array_non_uniform_indexing::Bool`
  * `descriptor_binding_uniform_buffer_update_after_bind::Bool`
  * `descriptor_binding_sampled_image_update_after_bind::Bool`
  * `descriptor_binding_storage_image_update_after_bind::Bool`
  * `descriptor_binding_storage_buffer_update_after_bind::Bool`
  * `descriptor_binding_uniform_texel_buffer_update_after_bind::Bool`
  * `descriptor_binding_storage_texel_buffer_update_after_bind::Bool`
  * `descriptor_binding_update_unused_while_pending::Bool`
  * `descriptor_binding_partially_bound::Bool`
  * `descriptor_binding_variable_descriptor_count::Bool`
  * `runtime_descriptor_array::Bool`
  * `sampler_filter_minmax::Bool`
  * `scalar_block_layout::Bool`
  * `imageless_framebuffer::Bool`
  * `uniform_buffer_standard_layout::Bool`
  * `shader_subgroup_extended_types::Bool`
  * `separate_depth_stencil_layouts::Bool`
  * `host_query_reset::Bool`
  * `timeline_semaphore::Bool`
  * `buffer_device_address::Bool`
  * `buffer_device_address_capture_replay::Bool`
  * `buffer_device_address_multi_device::Bool`
  * `vulkan_memory_model::Bool`
  * `vulkan_memory_model_device_scope::Bool`
  * `vulkan_memory_model_availability_visibility_chains::Bool`
  * `shader_output_viewport_index::Bool`
  * `shader_output_layer::Bool`
  * `subgroup_broadcast_dynamic_id::Bool`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceVulkan12Features.html)

```julia
PhysicalDeviceVulkan12Features(
    sampler_mirror_clamp_to_edge::Bool,
    draw_indirect_count::Bool,
    storage_buffer_8_bit_access::Bool,
    uniform_and_storage_buffer_8_bit_access::Bool,
    storage_push_constant_8::Bool,
    shader_buffer_int_64_atomics::Bool,
    shader_shared_int_64_atomics::Bool,
    shader_float_16::Bool,
    shader_int_8::Bool,
    descriptor_indexing::Bool,
    shader_input_attachment_array_dynamic_indexing::Bool,
    shader_uniform_texel_buffer_array_dynamic_indexing::Bool,
    shader_storage_texel_buffer_array_dynamic_indexing::Bool,
    shader_uniform_buffer_array_non_uniform_indexing::Bool,
    shader_sampled_image_array_non_uniform_indexing::Bool,
    shader_storage_buffer_array_non_uniform_indexing::Bool,
    shader_storage_image_array_non_uniform_indexing::Bool,
    shader_input_attachment_array_non_uniform_indexing::Bool,
    shader_uniform_texel_buffer_array_non_uniform_indexing::Bool,
    shader_storage_texel_buffer_array_non_uniform_indexing::Bool,
    descriptor_binding_uniform_buffer_update_after_bind::Bool,
    descriptor_binding_sampled_image_update_after_bind::Bool,
    descriptor_binding_storage_image_update_after_bind::Bool,
    descriptor_binding_storage_buffer_update_after_bind::Bool,
    descriptor_binding_uniform_texel_buffer_update_after_bind::Bool,
    descriptor_binding_storage_texel_buffer_update_after_bind::Bool,
    descriptor_binding_update_unused_while_pending::Bool,
    descriptor_binding_partially_bound::Bool,
    descriptor_binding_variable_descriptor_count::Bool,
    runtime_descriptor_array::Bool,
    sampler_filter_minmax::Bool,
    scalar_block_layout::Bool,
    imageless_framebuffer::Bool,
    uniform_buffer_standard_layout::Bool,
    shader_subgroup_extended_types::Bool,
    separate_depth_stencil_layouts::Bool,
    host_query_reset::Bool,
    timeline_semaphore::Bool,
    buffer_device_address::Bool,
    buffer_device_address_capture_replay::Bool,
    buffer_device_address_multi_device::Bool,
    vulkan_memory_model::Bool,
    vulkan_memory_model_device_scope::Bool,
    vulkan_memory_model_availability_visibility_chains::Bool,
    shader_output_viewport_index::Bool,
    shader_output_layer::Bool,
    subgroup_broadcast_dynamic_id::Bool;
    next
) -> Vulkan.PhysicalDeviceVulkan12Features

```
