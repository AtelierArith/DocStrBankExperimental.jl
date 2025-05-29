High-level wrapper for VkPhysicalDeviceFeatures.

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceFeatures.html)

```julia
struct PhysicalDeviceFeatures <: Vulkan.HighLevelStruct
```

  * `robust_buffer_access::Bool`
  * `full_draw_index_uint_32::Bool`
  * `image_cube_array::Bool`
  * `independent_blend::Bool`
  * `geometry_shader::Bool`
  * `tessellation_shader::Bool`
  * `sample_rate_shading::Bool`
  * `dual_src_blend::Bool`
  * `logic_op::Bool`
  * `multi_draw_indirect::Bool`
  * `draw_indirect_first_instance::Bool`
  * `depth_clamp::Bool`
  * `depth_bias_clamp::Bool`
  * `fill_mode_non_solid::Bool`
  * `depth_bounds::Bool`
  * `wide_lines::Bool`
  * `large_points::Bool`
  * `alpha_to_one::Bool`
  * `multi_viewport::Bool`
  * `sampler_anisotropy::Bool`
  * `texture_compression_etc_2::Bool`
  * `texture_compression_astc_ldr::Bool`
  * `texture_compression_bc::Bool`
  * `occlusion_query_precise::Bool`
  * `pipeline_statistics_query::Bool`
  * `vertex_pipeline_stores_and_atomics::Bool`
  * `fragment_stores_and_atomics::Bool`
  * `shader_tessellation_and_geometry_point_size::Bool`
  * `shader_image_gather_extended::Bool`
  * `shader_storage_image_extended_formats::Bool`
  * `shader_storage_image_multisample::Bool`
  * `shader_storage_image_read_without_format::Bool`
  * `shader_storage_image_write_without_format::Bool`
  * `shader_uniform_buffer_array_dynamic_indexing::Bool`
  * `shader_sampled_image_array_dynamic_indexing::Bool`
  * `shader_storage_buffer_array_dynamic_indexing::Bool`
  * `shader_storage_image_array_dynamic_indexing::Bool`
  * `shader_clip_distance::Bool`
  * `shader_cull_distance::Bool`
  * `shader_float_64::Bool`
  * `shader_int_64::Bool`
  * `shader_int_16::Bool`
  * `shader_resource_residency::Bool`
  * `shader_resource_min_lod::Bool`
  * `sparse_binding::Bool`
  * `sparse_residency_buffer::Bool`
  * `sparse_residency_image_2_d::Bool`
  * `sparse_residency_image_3_d::Bool`
  * `sparse_residency_2_samples::Bool`
  * `sparse_residency_4_samples::Bool`
  * `sparse_residency_8_samples::Bool`
  * `sparse_residency_16_samples::Bool`
  * `sparse_residency_aliased::Bool`
  * `variable_multisample_rate::Bool`
  * `inherited_queries::Bool`
