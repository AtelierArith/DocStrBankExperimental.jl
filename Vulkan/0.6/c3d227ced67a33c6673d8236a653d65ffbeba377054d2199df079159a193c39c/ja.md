拡張: VK*KHR*fragment*shading*rate

引数:

  * `fragment_size::Extent2D`
  * `combiner_ops::NTuple{2, FragmentShadingRateCombinerOpKHR}`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineFragmentShadingRateStateCreateInfoKHR.html)

```julia
PipelineFragmentShadingRateStateCreateInfoKHR(
    fragment_size::Vulkan.Extent2D,
    combiner_ops::Tuple{Vulkan.FragmentShadingRateCombinerOpKHR, Vulkan.FragmentShadingRateCombinerOpKHR};
    next
) -> Vulkan.PipelineFragmentShadingRateStateCreateInfoKHR

```
