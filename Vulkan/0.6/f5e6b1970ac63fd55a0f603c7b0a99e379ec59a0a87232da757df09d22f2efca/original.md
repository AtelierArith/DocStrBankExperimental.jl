High-level wrapper for VkPipelineFragmentShadingRateEnumStateCreateInfoNV.

Extension: VK_NV_fragment_shading_rate_enums

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineFragmentShadingRateEnumStateCreateInfoNV.html)

```julia
struct PipelineFragmentShadingRateEnumStateCreateInfoNV <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `shading_rate_type::Vulkan.FragmentShadingRateTypeNV`
  * `shading_rate::Vulkan.FragmentShadingRateNV`
  * `combiner_ops::Tuple{Vulkan.FragmentShadingRateCombinerOpKHR, Vulkan.FragmentShadingRateCombinerOpKHR}`
