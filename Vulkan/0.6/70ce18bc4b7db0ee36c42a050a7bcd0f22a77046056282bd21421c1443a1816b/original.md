Extension: VK_EXT_multisampled_render_to_single_sampled

Arguments:

  * `multisampled_render_to_single_sampled_enable::Bool`
  * `rasterization_samples::SampleCountFlag`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkMultisampledRenderToSingleSampledInfoEXT.html)

```julia
MultisampledRenderToSingleSampledInfoEXT(
    multisampled_render_to_single_sampled_enable::Bool,
    rasterization_samples::Vulkan.SampleCountFlag;
    next
) -> Vulkan.MultisampledRenderToSingleSampledInfoEXT

```
