Extension: VK_KHR_fragment_shading_rate

Arguments:

  * `fragment_size::_Extent2D`
  * `combiner_ops::NTuple{2, FragmentShadingRateCombinerOpKHR}`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineFragmentShadingRateStateCreateInfoKHR.html)

```julia
_PipelineFragmentShadingRateStateCreateInfoKHR(
    fragment_size::Vulkan._Extent2D,
    combiner_ops::Tuple{Vulkan.FragmentShadingRateCombinerOpKHR, Vulkan.FragmentShadingRateCombinerOpKHR};
    next
)

```
