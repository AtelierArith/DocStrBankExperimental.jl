High-level wrapper for VkRenderingFragmentShadingRateAttachmentInfoKHR.

Extension: VK_KHR_dynamic_rendering

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkRenderingFragmentShadingRateAttachmentInfoKHR.html)

```julia
struct RenderingFragmentShadingRateAttachmentInfoKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `image_view::Union{Ptr{Nothing}, Vulkan.ImageView}`
  * `image_layout::Vulkan.ImageLayout`
  * `shading_rate_attachment_texel_size::Vulkan.Extent2D`
