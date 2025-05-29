引数:

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
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceDescriptorIndexingFeatures.html)

```julia
PhysicalDeviceDescriptorIndexingFeatures(
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
    runtime_descriptor_array::Bool;
    next
) -> Vulkan.PhysicalDeviceDescriptorIndexingFeatures

```
