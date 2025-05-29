拡張: VK*NV*shading*rate*image

引数:

  * `sample_order_type::CoarseSampleOrderTypeNV`
  * `custom_sample_orders::Vector{CoarseSampleOrderCustomNV}`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineViewportCoarseSampleOrderStateCreateInfoNV.html)

```julia
PipelineViewportCoarseSampleOrderStateCreateInfoNV(
    sample_order_type::Vulkan.CoarseSampleOrderTypeNV,
    custom_sample_orders::AbstractArray;
    next
) -> Vulkan.PipelineViewportCoarseSampleOrderStateCreateInfoNV

```
