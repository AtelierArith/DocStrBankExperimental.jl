High-level wrapper for VkMultisampledRenderToSingleSampledInfoEXT.

Extension: VK_EXT_multisampled_render_to_single_sampled

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkMultisampledRenderToSingleSampledInfoEXT.html)

```julia
struct MultisampledRenderToSingleSampledInfoEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `multisampled_render_to_single_sampled_enable::Bool`
  * `rasterization_samples::Vulkan.SampleCountFlag`
