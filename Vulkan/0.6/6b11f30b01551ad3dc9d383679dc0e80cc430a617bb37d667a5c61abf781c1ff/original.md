High-level wrapper for VkPhysicalDeviceDescriptorBufferPropertiesEXT.

Extension: VK_EXT_descriptor_buffer

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceDescriptorBufferPropertiesEXT.html)

```julia
struct PhysicalDeviceDescriptorBufferPropertiesEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `combined_image_sampler_descriptor_single_array::Bool`
  * `bufferless_push_descriptors::Bool`
  * `allow_sampler_image_view_post_submit_creation::Bool`
  * `descriptor_buffer_offset_alignment::UInt64`
  * `max_descriptor_buffer_bindings::UInt32`
  * `max_resource_descriptor_buffer_bindings::UInt32`
  * `max_sampler_descriptor_buffer_bindings::UInt32`
  * `max_embedded_immutable_sampler_bindings::UInt32`
  * `max_embedded_immutable_samplers::UInt32`
  * `buffer_capture_replay_descriptor_data_size::UInt64`
  * `image_capture_replay_descriptor_data_size::UInt64`
  * `image_view_capture_replay_descriptor_data_size::UInt64`
  * `sampler_capture_replay_descriptor_data_size::UInt64`
  * `acceleration_structure_capture_replay_descriptor_data_size::UInt64`
  * `sampler_descriptor_size::UInt64`
  * `combined_image_sampler_descriptor_size::UInt64`
  * `sampled_image_descriptor_size::UInt64`
  * `storage_image_descriptor_size::UInt64`
  * `uniform_texel_buffer_descriptor_size::UInt64`
  * `robust_uniform_texel_buffer_descriptor_size::UInt64`
  * `storage_texel_buffer_descriptor_size::UInt64`
  * `robust_storage_texel_buffer_descriptor_size::UInt64`
  * `uniform_buffer_descriptor_size::UInt64`
  * `robust_uniform_buffer_descriptor_size::UInt64`
  * `storage_buffer_descriptor_size::UInt64`
  * `robust_storage_buffer_descriptor_size::UInt64`
  * `input_attachment_descriptor_size::UInt64`
  * `acceleration_structure_descriptor_size::UInt64`
  * `max_sampler_descriptor_buffer_range::UInt64`
  * `max_resource_descriptor_buffer_range::UInt64`
  * `sampler_descriptor_buffer_address_space_size::UInt64`
  * `resource_descriptor_buffer_address_space_size::UInt64`
  * `descriptor_buffer_address_space_size::UInt64`
