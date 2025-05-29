Arguments:

  * `src_image::Image`
  * `src_image_layout::ImageLayout`
  * `dst_image::Image`
  * `dst_image_layout::ImageLayout`
  * `regions::Vector{ImageBlit2}`
  * `filter::Filter`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkBlitImageInfo2.html)

```julia
BlitImageInfo2(
    src_image::Vulkan.Image,
    src_image_layout::Vulkan.ImageLayout,
    dst_image::Vulkan.Image,
    dst_image_layout::Vulkan.ImageLayout,
    regions::AbstractArray,
    filter::Vulkan.Filter;
    next
) -> Vulkan.BlitImageInfo2

```
