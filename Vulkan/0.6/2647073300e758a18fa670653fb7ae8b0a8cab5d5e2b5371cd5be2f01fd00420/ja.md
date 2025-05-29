引数:

  * `src_image::Image`
  * `src_image_layout::ImageLayout`
  * `dst_image::Image`
  * `dst_image_layout::ImageLayout`
  * `regions::Vector{_ImageBlit2}`
  * `filter::Filter`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkBlitImageInfo2.html)

```julia
_BlitImageInfo2(
    src_image,
    src_image_layout::Vulkan.ImageLayout,
    dst_image,
    dst_image_layout::Vulkan.ImageLayout,
    regions::AbstractArray,
    filter::Vulkan.Filter;
    next
) -> Vulkan._BlitImageInfo2

```
