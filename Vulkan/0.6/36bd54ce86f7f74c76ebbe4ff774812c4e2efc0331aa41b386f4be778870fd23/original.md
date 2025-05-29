Extension: VK_EXT_multisampled_render_to_single_sampled

Arguments:

  * `multisampled_render_to_single_sampled_enable::Bool`
  * `rasterization_samples::SampleCountFlag`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkMultisampledRenderToSingleSampledInfoEXT.html)

```julia
_MultisampledRenderToSingleSampledInfoEXT(
    multisampled_render_to_single_sampled_enable::Bool,
    rasterization_samples::Vulkan.SampleCountFlag;
    next
) -> Vulkan._MultisampledRenderToSingleSampledInfoEXT

```
