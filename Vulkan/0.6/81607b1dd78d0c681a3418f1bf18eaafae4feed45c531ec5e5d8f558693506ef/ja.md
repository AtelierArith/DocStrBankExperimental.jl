VkPhysicalDeviceExtendedDynamicState3FeaturesEXTの高レベルラッパー。

拡張: VK*EXT*extended*dynamic*state3

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceExtendedDynamicState3FeaturesEXT.html)

```julia
struct PhysicalDeviceExtendedDynamicState3FeaturesEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `extended_dynamic_state_3_tessellation_domain_origin::Bool`
  * `extended_dynamic_state_3_depth_clamp_enable::Bool`
  * `extended_dynamic_state_3_polygon_mode::Bool`
  * `extended_dynamic_state_3_rasterization_samples::Bool`
  * `extended_dynamic_state_3_sample_mask::Bool`
  * `extended_dynamic_state_3_alpha_to_coverage_enable::Bool`
  * `extended_dynamic_state_3_alpha_to_one_enable::Bool`
  * `extended_dynamic_state_3_logic_op_enable::Bool`
  * `extended_dynamic_state_3_color_blend_enable::Bool`
  * `extended_dynamic_state_3_color_blend_equation::Bool`
  * `extended_dynamic_state_3_color_write_mask::Bool`
  * `extended_dynamic_state_3_rasterization_stream::Bool`
  * `extended_dynamic_state_3_conservative_rasterization_mode::Bool`
  * `extended_dynamic_state_3_extra_primitive_overestimation_size::Bool`
  * `extended_dynamic_state_3_depth_clip_enable::Bool`
  * `extended_dynamic_state_3_sample_locations_enable::Bool`
  * `extended_dynamic_state_3_color_blend_advanced::Bool`
  * `extended_dynamic_state_3_provoking_vertex_mode::Bool`
  * `extended_dynamic_state_3_line_rasterization_mode::Bool`
  * `extended_dynamic_state_3_line_stipple_enable::Bool`
  * `extended_dynamic_state_3_depth_clip_negative_one_to_one::Bool`
  * `extended_dynamic_state_3_viewport_w_scaling_enable::Bool`
  * `extended_dynamic_state_3_viewport_swizzle::Bool`
  * `extended_dynamic_state_3_coverage_to_color_enable::Bool`
  * `extended_dynamic_state_3_coverage_to_color_location::Bool`
  * `extended_dynamic_state_3_coverage_modulation_mode::Bool`
  * `extended_dynamic_state_3_coverage_modulation_table_enable::Bool`
  * `extended_dynamic_state_3_coverage_modulation_table::Bool`
  * `extended_dynamic_state_3_coverage_reduction_mode::Bool`
  * `extended_dynamic_state_3_representative_fragment_test_enable::Bool`
  * `extended_dynamic_state_3_shading_rate_image_enable::Bool`
