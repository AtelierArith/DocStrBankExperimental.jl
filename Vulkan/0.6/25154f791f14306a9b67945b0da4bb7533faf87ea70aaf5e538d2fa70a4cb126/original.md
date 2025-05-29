Arguments:

  * `buffer_offset::UInt64`
  * `buffer_row_length::UInt32`
  * `buffer_image_height::UInt32`
  * `image_subresource::ImageSubresourceLayers`
  * `image_offset::Offset3D`
  * `image_extent::Extent3D`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkBufferImageCopy2.html)

```julia
BufferImageCopy2(
    buffer_offset::Integer,
    buffer_row_length::Integer,
    buffer_image_height::Integer,
    image_subresource::Vulkan.ImageSubresourceLayers,
    image_offset::Vulkan.Offset3D,
    image_extent::Vulkan.Extent3D;
    next
) -> Vulkan.BufferImageCopy2

```
