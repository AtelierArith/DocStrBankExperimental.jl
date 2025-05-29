拡張: VK*KHR*fragment*shading*rate

引数:

  * `min_fragment_shading_rate_attachment_texel_size::_Extent2D`
  * `max_fragment_shading_rate_attachment_texel_size::_Extent2D`
  * `max_fragment_shading_rate_attachment_texel_size_aspect_ratio::UInt32`
  * `primitive_fragment_shading_rate_with_multiple_viewports::Bool`
  * `layered_shading_rate_attachments::Bool`
  * `fragment_shading_rate_non_trivial_combiner_ops::Bool`
  * `max_fragment_size::_Extent2D`
  * `max_fragment_size_aspect_ratio::UInt32`
  * `max_fragment_shading_rate_coverage_samples::UInt32`
  * `max_fragment_shading_rate_rasterization_samples::SampleCountFlag`
  * `fragment_shading_rate_with_shader_depth_stencil_writes::Bool`
  * `fragment_shading_rate_with_sample_mask::Bool`
  * `fragment_shading_rate_with_shader_sample_mask::Bool`
  * `fragment_shading_rate_with_conservative_rasterization::Bool`
  * `fragment_shading_rate_with_fragment_shader_interlock::Bool`
  * `fragment_shading_rate_with_custom_sample_locations::Bool`
  * `fragment_shading_rate_strict_multiply_combiner::Bool`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceFragmentShadingRatePropertiesKHR.html)

```julia
_PhysicalDeviceFragmentShadingRatePropertiesKHR(
    min_fragment_shading_rate_attachment_texel_size::Vulkan._Extent2D,
    max_fragment_shading_rate_attachment_texel_size::Vulkan._Extent2D,
    max_fragment_shading_rate_attachment_texel_size_aspect_ratio::Integer,
    primitive_fragment_shading_rate_with_multiple_viewports::Bool,
    layered_shading_rate_attachments::Bool,
    fragment_shading_rate_non_trivial_combiner_ops::Bool,
    max_fragment_size::Vulkan._Extent2D,
    max_fragment_size_aspect_ratio::Integer,
    max_fragment_shading_rate_coverage_samples::Integer,
    max_fragment_shading_rate_rasterization_samples::Vulkan.SampleCountFlag,
    fragment_shading_rate_with_shader_depth_stencil_writes::Bool,
    fragment_shading_rate_with_sample_mask::Bool,
    fragment_shading_rate_with_shader_sample_mask::Bool,
    fragment_shading_rate_with_conservative_rasterization::Bool,
    fragment_shading_rate_with_fragment_shader_interlock::Bool,
    fragment_shading_rate_with_custom_sample_locations::Bool,
    fragment_shading_rate_strict_multiply_combiner::Bool;
    next
) -> Vulkan._PhysicalDeviceFragmentShadingRatePropertiesKHR

```
