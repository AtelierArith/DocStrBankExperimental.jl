High-level wrapper for VkPipelineViewportCoarseSampleOrderStateCreateInfoNV.

Extension: VK_NV_shading_rate_image

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineViewportCoarseSampleOrderStateCreateInfoNV.html)

```julia
struct PipelineViewportCoarseSampleOrderStateCreateInfoNV <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `sample_order_type::Vulkan.CoarseSampleOrderTypeNV`
  * `custom_sample_orders::Vector{Vulkan.CoarseSampleOrderCustomNV}`
