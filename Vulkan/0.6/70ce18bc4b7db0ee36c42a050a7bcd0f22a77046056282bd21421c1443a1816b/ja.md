拡張: VK*EXT*multisampled*render*to*single*sampled

引数:

  * `multisampled_render_to_single_sampled_enable::Bool`
  * `rasterization_samples::SampleCountFlag`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkMultisampledRenderToSingleSampledInfoEXT.html)

```julia
MultisampledRenderToSingleSampledInfoEXT(
    multisampled_render_to_single_sampled_enable::Bool,
    rasterization_samples::Vulkan.SampleCountFlag;
    next
) -> Vulkan.MultisampledRenderToSingleSampledInfoEXT

```
