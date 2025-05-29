引数:

  * `max_update_after_bind_descriptors_in_all_pools::UInt32`
  * `shader_uniform_buffer_array_non_uniform_indexing_native::Bool`
  * `shader_sampled_image_array_non_uniform_indexing_native::Bool`
  * `shader_storage_buffer_array_non_uniform_indexing_native::Bool`
  * `shader_storage_image_array_non_uniform_indexing_native::Bool`
  * `shader_input_attachment_array_non_uniform_indexing_native::Bool`
  * `robust_buffer_access_update_after_bind::Bool`
  * `quad_divergent_implicit_lod::Bool`
  * `max_per_stage_descriptor_update_after_bind_samplers::UInt32`
  * `max_per_stage_descriptor_update_after_bind_uniform_buffers::UInt32`
  * `max_per_stage_descriptor_update_after_bind_storage_buffers::UInt32`
  * `max_per_stage_descriptor_update_after_bind_sampled_images::UInt32`
  * `max_per_stage_descriptor_update_after_bind_storage_images::UInt32`
  * `max_per_stage_descriptor_update_after_bind_input_attachments::UInt32`
  * `max_per_stage_update_after_bind_resources::UInt32`
  * `max_descriptor_set_update_after_bind_samplers::UInt32`
  * `max_descriptor_set_update_after_bind_uniform_buffers::UInt32`
  * `max_descriptor_set_update_after_bind_uniform_buffers_dynamic::UInt32`
  * `max_descriptor_set_update_after_bind_storage_buffers::UInt32`
  * `max_descriptor_set_update_after_bind_storage_buffers_dynamic::UInt32`
  * `max_descriptor_set_update_after_bind_sampled_images::UInt32`
  * `max_descriptor_set_update_after_bind_storage_images::UInt32`
  * `max_descriptor_set_update_after_bind_input_attachments::UInt32`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceDescriptorIndexingProperties.html)

```julia
_PhysicalDeviceDescriptorIndexingProperties(
    max_update_after_bind_descriptors_in_all_pools::Integer,
    shader_uniform_buffer_array_non_uniform_indexing_native::Bool,
    shader_sampled_image_array_non_uniform_indexing_native::Bool,
    shader_storage_buffer_array_non_uniform_indexing_native::Bool,
    shader_storage_image_array_non_uniform_indexing_native::Bool,
    shader_input_attachment_array_non_uniform_indexing_native::Bool,
    robust_buffer_access_update_after_bind::Bool,
    quad_divergent_implicit_lod::Bool,
    max_per_stage_descriptor_update_after_bind_samplers::Integer,
    max_per_stage_descriptor_update_after_bind_uniform_buffers::Integer,
    max_per_stage_descriptor_update_after_bind_storage_buffers::Integer,
    max_per_stage_descriptor_update_after_bind_sampled_images::Integer,
    max_per_stage_descriptor_update_after_bind_storage_images::Integer,
    max_per_stage_descriptor_update_after_bind_input_attachments::Integer,
    max_per_stage_update_after_bind_resources::Integer,
    max_descriptor_set_update_after_bind_samplers::Integer,
    max_descriptor_set_update_after_bind_uniform_buffers::Integer,
    max_descriptor_set_update_after_bind_uniform_buffers_dynamic::Integer,
    max_descriptor_set_update_after_bind_storage_buffers::Integer,
    max_descriptor_set_update_after_bind_storage_buffers_dynamic::Integer,
    max_descriptor_set_update_after_bind_sampled_images::Integer,
    max_descriptor_set_update_after_bind_storage_images::Integer,
    max_descriptor_set_update_after_bind_input_attachments::Integer;
    next
) -> Vulkan._PhysicalDeviceDescriptorIndexingProperties

```
