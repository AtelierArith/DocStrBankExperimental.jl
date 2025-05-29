Arguments:

  * `src_subresource::ImageSubresourceLayers`
  * `src_offset::Offset3D`
  * `dst_subresource::ImageSubresourceLayers`
  * `dst_offset::Offset3D`
  * `extent::Extent3D`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkImageCopy2.html)

```julia
ImageCopy2(
    src_subresource::Vulkan.ImageSubresourceLayers,
    src_offset::Vulkan.Offset3D,
    dst_subresource::Vulkan.ImageSubresourceLayers,
    dst_offset::Vulkan.Offset3D,
    extent::Vulkan.Extent3D;
    next
) -> Vulkan.ImageCopy2

```
