Arguments:

  * `buffer_offset::UInt64`
  * `buffer_row_length::UInt32`
  * `buffer_image_height::UInt32`
  * `image_subresource::_ImageSubresourceLayers`
  * `image_offset::_Offset3D`
  * `image_extent::_Extent3D`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkBufferImageCopy.html)

```julia
_BufferImageCopy(
    buffer_offset::Integer,
    buffer_row_length::Integer,
    buffer_image_height::Integer,
    image_subresource::Vulkan._ImageSubresourceLayers,
    image_offset::Vulkan._Offset3D,
    image_extent::Vulkan._Extent3D
) -> Vulkan._BufferImageCopy

```
