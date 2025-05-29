Arguments:

  * `src_image::Image`
  * `src_image_layout::ImageLayout`
  * `dst_image::Image`
  * `dst_image_layout::ImageLayout`
  * `regions::Vector{_ImageCopy2}`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCopyImageInfo2.html)

```julia
_CopyImageInfo2(
    src_image,
    src_image_layout::Vulkan.ImageLayout,
    dst_image,
    dst_image_layout::Vulkan.ImageLayout,
    regions::AbstractArray;
    next
) -> Vulkan._CopyImageInfo2

```
