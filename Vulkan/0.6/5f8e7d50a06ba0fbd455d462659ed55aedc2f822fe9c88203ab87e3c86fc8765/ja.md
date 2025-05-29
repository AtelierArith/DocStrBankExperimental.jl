引数:

  * `max_image_dimension_1_d::UInt32`
  * `max_image_dimension_2_d::UInt32`
  * `max_image_dimension_3_d::UInt32`
  * `max_image_dimension_cube::UInt32`
  * `max_image_array_layers::UInt32`
  * `max_texel_buffer_elements::UInt32`
  * `max_uniform_buffer_range::UInt32`
  * `max_storage_buffer_range::UInt32`
  * `max_push_constants_size::UInt32`
  * `max_memory_allocation_count::UInt32`
  * `max_sampler_allocation_count::UInt32`
  * `buffer_image_granularity::UInt64`
  * `sparse_address_space_size::UInt64`
  * `max_bound_descriptor_sets::UInt32`
  * `max_per_stage_descriptor_samplers::UInt32`
  * `max_per_stage_descriptor_uniform_buffers::UInt32`
  * `max_per_stage_descriptor_storage_buffers::UInt32`
  * `max_per_stage_descriptor_sampled_images::UInt32`
  * `max_per_stage_descriptor_storage_images::UInt32`
  * `max_per_stage_descriptor_input_attachments::UInt32`
  * `max_per_stage_resources::UInt32`
  * `max_descriptor_set_samplers::UInt32`
  * `max_descriptor_set_uniform_buffers::UInt32`
  * `max_descriptor_set_uniform_buffers_dynamic::UInt32`
  * `max_descriptor_set_storage_buffers::UInt32`
  * `max_descriptor_set_storage_buffers_dynamic::UInt32`
  * `max_descriptor_set_sampled_images::UInt32`
  * `max_descriptor_set_storage_images::UInt32`
  * `max_descriptor_set_input_attachments::UInt32`
  * `max_vertex_input_attributes::UInt32`
  * `max_vertex_input_bindings::UInt32`
  * `max_vertex_input_attribute_offset::UInt32`
  * `max_vertex_input_binding_stride::UInt32`
  * `max_vertex_output_components::UInt32`
  * `max_tessellation_generation_level::UInt32`
  * `max_tessellation_patch_size::UInt32`
  * `max_tessellation_control_per_vertex_input_components::UInt32`
  * `max_tessellation_control_per_vertex_output_components::UInt32`
  * `max_tessellation_control_per_patch_output_components::UInt32`
  * `max_tessellation_control_total_output_components::UInt32`
  * `max_tessellation_evaluation_input_components::UInt32`
  * `max_tessellation_evaluation_output_components::UInt32`
  * `max_geometry_shader_invocations::UInt32`
  * `max_geometry_input_components::UInt32`
  * `max_geometry_output_components::UInt32`
  * `max_geometry_output_vertices::UInt32`
  * `max_geometry_total_output_components::UInt32`
  * `max_fragment_input_components::UInt32`
  * `max_fragment_output_attachments::UInt32`
  * `max_fragment_dual_src_attachments::UInt32`
  * `max_fragment_combined_output_resources::UInt32`
  * `max_compute_shared_memory_size::UInt32`
  * `max_compute_work_group_count::NTuple{3, UInt32}`
  * `max_compute_work_group_invocations::UInt32`
  * `max_compute_work_group_size::NTuple{3, UInt32}`
  * `sub_pixel_precision_bits::UInt32`
  * `sub_texel_precision_bits::UInt32`
  * `mipmap_precision_bits::UInt32`
  * `max_draw_indexed_index_value::UInt32`
  * `max_draw_indirect_count::UInt32`
  * `max_sampler_lod_bias::Float32`
  * `max_sampler_anisotropy::Float32`
  * `max_viewports::UInt32`
  * `max_viewport_dimensions::NTuple{2, UInt32}`
  * `viewport_bounds_range::NTuple{2, Float32}`
  * `viewport_sub_pixel_bits::UInt32`
  * `min_memory_map_alignment::UInt`
  * `min_texel_buffer_offset_alignment::UInt64`
  * `min_uniform_buffer_offset_alignment::UInt64`
  * `min_storage_buffer_offset_alignment::UInt64`
  * `min_texel_offset::Int32`
  * `max_texel_offset::UInt32`
  * `min_texel_gather_offset::Int32`
  * `max_texel_gather_offset::UInt32`
  * `min_interpolation_offset::Float32`
  * `max_interpolation_offset::Float32`
  * `sub_pixel_interpolation_offset_bits::UInt32`
  * `max_framebuffer_width::UInt32`
  * `max_framebuffer_height::UInt32`
  * `max_framebuffer_layers::UInt32`
  * `max_color_attachments::UInt32`
  * `max_sample_mask_words::UInt32`
  * `timestamp_compute_and_graphics::Bool`
  * `timestamp_period::Float32`
  * `max_clip_distances::UInt32`
  * `max_cull_distances::UInt32`
  * `max_combined_clip_and_cull_distances::UInt32`
  * `discrete_queue_priorities::UInt32`
  * `point_size_range::NTuple{2, Float32}`
  * `line_width_range::NTuple{2, Float32}`
  * `point_size_granularity::Float32`
  * `line_width_granularity::Float32`
  * `strict_lines::Bool`
  * `standard_sample_locations::Bool`
  * `optimal_buffer_copy_offset_alignment::UInt64`
  * `optimal_buffer_copy_row_pitch_alignment::UInt64`
  * `non_coherent_atom_size::UInt64`
  * `framebuffer_color_sample_counts::SampleCountFlag`: デフォルトは `0`
  * `framebuffer_depth_sample_counts::SampleCountFlag`: デフォルトは `0`
  * `framebuffer_stencil_sample_counts::SampleCountFlag`: デフォルトは `0`
  * `framebuffer_no_attachments_sample_counts::SampleCountFlag`: デフォルトは `0`
  * `sampled_image_color_sample_counts::SampleCountFlag`: デフォルトは `0`
  * `sampled_image_integer_sample_counts::SampleCountFlag`: デフォルトは `0`
  * `sampled_image_depth_sample_counts::SampleCountFlag`: デフォルトは `0`
  * `sampled_image_stencil_sample_counts::SampleCountFlag`: デフォルトは `0`
  * `storage_image_sample_counts::SampleCountFlag`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceLimits.html)

```julia
_PhysicalDeviceLimits(
    max_image_dimension_1_d::Integer,
    max_image_dimension_2_d::Integer,
    max_image_dimension_3_d::Integer,
    max_image_dimension_cube::Integer,
    max_image_array_layers::Integer,
    max_texel_buffer_elements::Integer,
    max_uniform_buffer_range::Integer,
    max_storage_buffer_range::Integer,
    max_push_constants_size::Integer,
    max_memory_allocation_count::Integer,
    max_sampler_allocation_count::Integer,
    buffer_image_granularity::Integer,
    sparse_address_space_size::Integer,
    max_bound_descriptor_sets::Integer,
    max_per_stage_descriptor_samplers::Integer,
    max_per_stage_descriptor_uniform_buffers::Integer,
    max_per_stage_descriptor_storage_buffers::Integer,
    max_per_stage_descriptor_sampled_images::Integer,
    max_per_stage_descriptor_storage_images::Integer,
    max_per_stage_descriptor_input_attachments::Integer,
    max_per_stage_resources::Integer,
    max_descriptor_set_samplers::Integer,
    max_descriptor_set_uniform_buffers::Integer,
    max_descriptor_set_uniform_buffers_dynamic::Integer,
    max_descriptor_set_storage_buffers::Integer,
    max_descriptor_set_storage_buffers_dynamic::Integer,
    max_descriptor_set_sampled_images::Integer,
    max_descriptor_set_storage_images::Integer,
    max_descriptor_set_input_attachments::Integer,
    max_vertex_input_attributes::Integer,
    max_vertex_input_bindings::Integer,
    max_vertex_input_attribute_offset::Integer,
    max_vertex_input_binding_stride::Integer,
    max_vertex_output_components::Integer,
    max_tessellation_generation_level::Integer,
    max_tessellation_patch_size::Integer,
    max_tessellation_control_per_vertex_input_components::Integer,
    max_tessellation_control_per_vertex_output_components::Integer,
    max_tessellation_control_per_patch_output_components::Integer,
    max_tessellation_control_total_output_components::Integer,
    max_tessellation_evaluation_input_components::Integer,
    max_tessellation_evaluation_output_components::Integer,
    max_geometry_shader_invocations::Integer,
    max_geometry_input_components::Integer,
    max_geometry_output_components::Integer,
    max_geometry_output_vertices::Integer,
    max_geometry_total_output_components::Integer,
    max_fragment_input_components::Integer,
    max_fragment_output_attachments::Integer,
    max_fragment_dual_src_attachments::Integer,
    max_fragment_combined_output_resources::Integer,
    max_compute_shared_memory_size::Integer,
    max_compute_work_group_count::Tuple{UInt32, UInt32, UInt32},
    max_compute_work_group_invocations::Integer,
    max_compute_work_group_size::Tuple{UInt32, UInt32, UInt32},
    sub_pixel_precision_bits::Integer,
    sub_texel_precision_bits::Integer,
    mipmap_precision_bits::Integer,
    max_draw_indexed_index_value::Integer,
    max_draw_indirect_count::Integer,
    max_sampler_lod_bias::Real,
    max_sampler_anisotropy::Real,
    max_viewports::Integer,
    max_viewport_dimensions::Tuple{UInt32, UInt32},
    viewport_bounds_range::Tuple{Float32, Float32},
    viewport_sub_pixel_bits::Integer,
    min_memory_map_alignment::Integer,
    min_texel_buffer_offset_alignment::Integer,
    min_uniform_buffer_offset_alignment::Integer,
    min_storage_buffer_offset_alignment::Integer,
    min_texel_offset::Integer,
    max_texel_offset::Integer,
    min_texel_gather_offset::Integer,
    max_texel_gather_offset::Integer,
    min_interpolation_offset::Real,
    max_interpolation_offset::Real,
    sub_pixel_interpolation_offset_bits::Integer,
    max_framebuffer_width::Integer,
    max_framebuffer_height::Integer,
    max_framebuffer_layers::Integer,
    max_color_attachments::Integer,
    max_sample_mask_words::Integer,
    timestamp_compute_and_graphics::Bool,
    timestamp_period::Real,
    max_clip_distances::Integer,
    max_cull_distances::Integer,
    max_combined_clip_and_cull_distances::Integer,
    discrete_queue_priorities::Integer,
    point_size_range::Tuple{Float32, Float32},
    line_width_range::Tuple{Float32, Float32},
    point_size_granularity::Real,
    line_width_granularity::Real,
    strict_lines::Bool,
    standard_sample_locations::Bool,
    optimal_buffer_copy_offset_alignment::Integer,
    optimal_buffer_copy_row_pitch_alignment::Integer,
    non_coherent_atom_size::Integer;
    framebuffer_color_sample_counts,
    framebuffer_depth_sample_counts,
    framebuffer_stencil_sample_counts,
    framebuffer_no_attachments_sample_counts,
    sampled_image_color_sample_counts,
    sampled_image_integer_sample_counts,
    sampled_image_depth_sample_counts,
    sampled_image_stencil_sample_counts,
    storage_image_sample_counts
) -> Vulkan._PhysicalDeviceLimits

```
