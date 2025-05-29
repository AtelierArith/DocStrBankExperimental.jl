High-level wrapper for VkPhysicalDeviceVulkan12Properties.

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceVulkan12Properties.html)

```julia
struct PhysicalDeviceVulkan12Properties <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `driver_id::Vulkan.DriverId`
  * `driver_name::String`
  * `driver_info::String`
  * `conformance_version::Vulkan.ConformanceVersion`
  * `denorm_behavior_independence::Vulkan.ShaderFloatControlsIndependence`
  * `rounding_mode_independence::Vulkan.ShaderFloatControlsIndependence`
  * `shader_signed_zero_inf_nan_preserve_float_16::Bool`
  * `shader_signed_zero_inf_nan_preserve_float_32::Bool`
  * `shader_signed_zero_inf_nan_preserve_float_64::Bool`
  * `shader_denorm_preserve_float_16::Bool`
  * `shader_denorm_preserve_float_32::Bool`
  * `shader_denorm_preserve_float_64::Bool`
  * `shader_denorm_flush_to_zero_float_16::Bool`
  * `shader_denorm_flush_to_zero_float_32::Bool`
  * `shader_denorm_flush_to_zero_float_64::Bool`
  * `shader_rounding_mode_rte_float_16::Bool`
  * `shader_rounding_mode_rte_float_32::Bool`
  * `shader_rounding_mode_rte_float_64::Bool`
  * `shader_rounding_mode_rtz_float_16::Bool`
  * `shader_rounding_mode_rtz_float_32::Bool`
  * `shader_rounding_mode_rtz_float_64::Bool`
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
  * `supported_depth_resolve_modes::Vulkan.ResolveModeFlag`
  * `supported_stencil_resolve_modes::Vulkan.ResolveModeFlag`
  * `independent_resolve_none::Bool`
  * `independent_resolve::Bool`
  * `filter_minmax_single_component_formats::Bool`
  * `filter_minmax_image_component_mapping::Bool`
  * `max_timeline_semaphore_value_difference::UInt64`
  * `framebuffer_integer_color_sample_counts::Vulkan.SampleCountFlag`
