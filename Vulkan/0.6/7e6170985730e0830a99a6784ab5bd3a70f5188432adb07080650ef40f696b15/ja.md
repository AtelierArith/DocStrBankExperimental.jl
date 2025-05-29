VkPipelineViewportCoarseSampleOrderStateCreateInfoNVの高レベルラッパー。

拡張: VK*NV*shading*rate*image

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineViewportCoarseSampleOrderStateCreateInfoNV.html)

```julia
struct PipelineViewportCoarseSampleOrderStateCreateInfoNV <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `sample_order_type::Vulkan.CoarseSampleOrderTypeNV`
  * `custom_sample_orders::Vector{Vulkan.CoarseSampleOrderCustomNV}`
