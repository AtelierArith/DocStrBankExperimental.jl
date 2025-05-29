Extension: VK_NV_fragment_shading_rate_enums

Arguments:

  * `shading_rate_type::FragmentShadingRateTypeNV`
  * `shading_rate::FragmentShadingRateNV`
  * `combiner_ops::NTuple{2, FragmentShadingRateCombinerOpKHR}`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineFragmentShadingRateEnumStateCreateInfoNV.html)

```julia
_PipelineFragmentShadingRateEnumStateCreateInfoNV(
    shading_rate_type::Vulkan.FragmentShadingRateTypeNV,
    shading_rate::Vulkan.FragmentShadingRateNV,
    combiner_ops::Tuple{Vulkan.FragmentShadingRateCombinerOpKHR, Vulkan.FragmentShadingRateCombinerOpKHR};
    next
)

```
