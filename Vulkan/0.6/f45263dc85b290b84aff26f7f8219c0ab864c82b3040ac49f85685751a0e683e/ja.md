拡張: VK*KHR*dynamic_rendering

引数:

  * `image_view::ImageView`
  * `image_layout::ImageLayout`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkRenderingFragmentDensityMapAttachmentInfoEXT.html)

```julia
RenderingFragmentDensityMapAttachmentInfoEXT(
    image_view::Vulkan.ImageView,
    image_layout::Vulkan.ImageLayout;
    next
) -> Vulkan.RenderingFragmentDensityMapAttachmentInfoEXT

```
