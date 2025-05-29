拡張: VK*KHR*fragment*shading*rate

引数:

  * `fragment_size::_Extent2D`
  * `combiner_ops::NTuple{2, FragmentShadingRateCombinerOpKHR}`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineFragmentShadingRateStateCreateInfoKHR.html)

```julia
_PipelineFragmentShadingRateStateCreateInfoKHR(
    fragment_size::Vulkan._Extent2D,
    combiner_ops::Tuple{Vulkan.FragmentShadingRateCombinerOpKHR, Vulkan.FragmentShadingRateCombinerOpKHR};
    next
)

```
