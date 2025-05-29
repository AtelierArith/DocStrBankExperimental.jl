拡張: VK*KHR*dynamic_rendering

引数:

  * `image_layout::ImageLayout`
  * `shading_rate_attachment_texel_size::Extent2D`
  * `next::Any`: デフォルトは `C_NULL`
  * `image_view::ImageView`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkRenderingFragmentShadingRateAttachmentInfoKHR.html)

```julia
RenderingFragmentShadingRateAttachmentInfoKHR(
    image_layout::Vulkan.ImageLayout,
    shading_rate_attachment_texel_size::Vulkan.Extent2D;
    next,
    image_view
) -> Vulkan.RenderingFragmentShadingRateAttachmentInfoKHR

```
