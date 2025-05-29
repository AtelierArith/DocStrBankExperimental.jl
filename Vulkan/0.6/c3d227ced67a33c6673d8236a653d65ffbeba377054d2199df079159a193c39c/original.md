Extension: VK_KHR_fragment_shading_rate

Arguments:

  * `fragment_size::Extent2D`
  * `combiner_ops::NTuple{2, FragmentShadingRateCombinerOpKHR}`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineFragmentShadingRateStateCreateInfoKHR.html)

```julia
PipelineFragmentShadingRateStateCreateInfoKHR(
    fragment_size::Vulkan.Extent2D,
    combiner_ops::Tuple{Vulkan.FragmentShadingRateCombinerOpKHR, Vulkan.FragmentShadingRateCombinerOpKHR};
    next
) -> Vulkan.PipelineFragmentShadingRateStateCreateInfoKHR

```
