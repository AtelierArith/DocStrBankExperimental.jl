Extension: VK_NV_shading_rate_image

Arguments:

  * `sample_order_type::CoarseSampleOrderTypeNV`
  * `custom_sample_orders::Vector{CoarseSampleOrderCustomNV}`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineViewportCoarseSampleOrderStateCreateInfoNV.html)

```julia
PipelineViewportCoarseSampleOrderStateCreateInfoNV(
    sample_order_type::Vulkan.CoarseSampleOrderTypeNV,
    custom_sample_orders::AbstractArray;
    next
) -> Vulkan.PipelineViewportCoarseSampleOrderStateCreateInfoNV

```
