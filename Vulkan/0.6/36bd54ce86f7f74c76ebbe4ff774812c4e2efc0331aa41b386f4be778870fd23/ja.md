拡張: VK*EXT*multisampled*render*to*single*sampled

引数:

  * `multisampled_render_to_single_sampled_enable::Bool`
  * `rasterization_samples::SampleCountFlag`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkMultisampledRenderToSingleSampledInfoEXT.html)

```julia
_MultisampledRenderToSingleSampledInfoEXT(
    multisampled_render_to_single_sampled_enable::Bool,
    rasterization_samples::Vulkan.SampleCountFlag;
    next
) -> Vulkan._MultisampledRenderToSingleSampledInfoEXT

```
