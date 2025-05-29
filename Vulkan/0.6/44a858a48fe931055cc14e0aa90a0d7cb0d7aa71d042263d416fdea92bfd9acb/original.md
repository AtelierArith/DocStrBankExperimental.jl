Extension: VK_EXT_descriptor_buffer

Arguments:

  * `combined_image_sampler_descriptor_single_array::Bool`
  * `bufferless_push_descriptors::Bool`
  * `allow_sampler_image_view_post_submit_creation::Bool`
  * `descriptor_buffer_offset_alignment::UInt64`
  * `max_descriptor_buffer_bindings::UInt32`
  * `max_resource_descriptor_buffer_bindings::UInt32`
  * `max_sampler_descriptor_buffer_bindings::UInt32`
  * `max_embedded_immutable_sampler_bindings::UInt32`
  * `max_embedded_immutable_samplers::UInt32`
  * `buffer_capture_replay_descriptor_data_size::UInt`
  * `image_capture_replay_descriptor_data_size::UInt`
  * `image_view_capture_replay_descriptor_data_size::UInt`
  * `sampler_capture_replay_descriptor_data_size::UInt`
  * `acceleration_structure_capture_replay_descriptor_data_size::UInt`
  * `sampler_descriptor_size::UInt`
  * `combined_image_sampler_descriptor_size::UInt`
  * `sampled_image_descriptor_size::UInt`
  * `storage_image_descriptor_size::UInt`
  * `uniform_texel_buffer_descriptor_size::UInt`
  * `robust_uniform_texel_buffer_descriptor_size::UInt`
  * `storage_texel_buffer_descriptor_size::UInt`
  * `robust_storage_texel_buffer_descriptor_size::UInt`
  * `uniform_buffer_descriptor_size::UInt`
  * `robust_uniform_buffer_descriptor_size::UInt`
  * `storage_buffer_descriptor_size::UInt`
  * `robust_storage_buffer_descriptor_size::UInt`
  * `input_attachment_descriptor_size::UInt`
  * `acceleration_structure_descriptor_size::UInt`
  * `max_sampler_descriptor_buffer_range::UInt64`
  * `max_resource_descriptor_buffer_range::UInt64`
  * `sampler_descriptor_buffer_address_space_size::UInt64`
  * `resource_descriptor_buffer_address_space_size::UInt64`
  * `descriptor_buffer_address_space_size::UInt64`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceDescriptorBufferPropertiesEXT.html)

```julia
PhysicalDeviceDescriptorBufferPropertiesEXT(
    combined_image_sampler_descriptor_single_array::Bool,
    bufferless_push_descriptors::Bool,
    allow_sampler_image_view_post_submit_creation::Bool,
    descriptor_buffer_offset_alignment::Integer,
    max_descriptor_buffer_bindings::Integer,
    max_resource_descriptor_buffer_bindings::Integer,
    max_sampler_descriptor_buffer_bindings::Integer,
    max_embedded_immutable_sampler_bindings::Integer,
    max_embedded_immutable_samplers::Integer,
    buffer_capture_replay_descriptor_data_size::Integer,
    image_capture_replay_descriptor_data_size::Integer,
    image_view_capture_replay_descriptor_data_size::Integer,
    sampler_capture_replay_descriptor_data_size::Integer,
    acceleration_structure_capture_replay_descriptor_data_size::Integer,
    sampler_descriptor_size::Integer,
    combined_image_sampler_descriptor_size::Integer,
    sampled_image_descriptor_size::Integer,
    storage_image_descriptor_size::Integer,
    uniform_texel_buffer_descriptor_size::Integer,
    robust_uniform_texel_buffer_descriptor_size::Integer,
    storage_texel_buffer_descriptor_size::Integer,
    robust_storage_texel_buffer_descriptor_size::Integer,
    uniform_buffer_descriptor_size::Integer,
    robust_uniform_buffer_descriptor_size::Integer,
    storage_buffer_descriptor_size::Integer,
    robust_storage_buffer_descriptor_size::Integer,
    input_attachment_descriptor_size::Integer,
    acceleration_structure_descriptor_size::Integer,
    max_sampler_descriptor_buffer_range::Integer,
    max_resource_descriptor_buffer_range::Integer,
    sampler_descriptor_buffer_address_space_size::Integer,
    resource_descriptor_buffer_address_space_size::Integer,
    descriptor_buffer_address_space_size::Integer;
    next
) -> Vulkan.PhysicalDeviceDescriptorBufferPropertiesEXT

```
