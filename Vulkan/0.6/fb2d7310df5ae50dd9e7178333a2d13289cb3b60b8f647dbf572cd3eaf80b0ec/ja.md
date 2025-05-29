高レベルのラッパー VkPipelineFragmentShadingRateStateCreateInfoKHR。

拡張: VK*KHR*fragment*shading*rate

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineFragmentShadingRateStateCreateInfoKHR.html)

```julia
struct PipelineFragmentShadingRateStateCreateInfoKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `fragment_size::Vulkan.Extent2D`
  * `combiner_ops::Tuple{Vulkan.FragmentShadingRateCombinerOpKHR, Vulkan.FragmentShadingRateCombinerOpKHR}`
