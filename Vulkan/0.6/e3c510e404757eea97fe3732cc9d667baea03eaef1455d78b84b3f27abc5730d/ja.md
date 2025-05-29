VkMultisampledRenderToSingleSampledInfoEXTの高レベルラッパー。

拡張: VK*EXT*multisampled*render*to*single*sampled

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkMultisampledRenderToSingleSampledInfoEXT.html)

```julia
struct MultisampledRenderToSingleSampledInfoEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `multisampled_render_to_single_sampled_enable::Bool`
  * `rasterization_samples::Vulkan.SampleCountFlag`
