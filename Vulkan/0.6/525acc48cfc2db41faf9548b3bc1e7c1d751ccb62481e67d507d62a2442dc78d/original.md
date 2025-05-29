Extension: VK_KHR_dynamic_rendering

Arguments:

  * `image_layout::ImageLayout`
  * `shading_rate_attachment_texel_size::Extent2D`
  * `next::Any`: defaults to `C_NULL`
  * `image_view::ImageView`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkRenderingFragmentShadingRateAttachmentInfoKHR.html)

```julia
RenderingFragmentShadingRateAttachmentInfoKHR(
    image_layout::Vulkan.ImageLayout,
    shading_rate_attachment_texel_size::Vulkan.Extent2D;
    next,
    image_view
) -> Vulkan.RenderingFragmentShadingRateAttachmentInfoKHR

```
