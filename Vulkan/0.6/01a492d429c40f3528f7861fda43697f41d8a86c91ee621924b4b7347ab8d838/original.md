Extension: VK_KHR_dynamic_rendering

Arguments:

  * `image_view::ImageView`
  * `image_layout::ImageLayout`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkRenderingFragmentDensityMapAttachmentInfoEXT.html)

```julia
_RenderingFragmentDensityMapAttachmentInfoEXT(
    image_view,
    image_layout::Vulkan.ImageLayout;
    next
) -> Vulkan._RenderingFragmentDensityMapAttachmentInfoEXT

```
