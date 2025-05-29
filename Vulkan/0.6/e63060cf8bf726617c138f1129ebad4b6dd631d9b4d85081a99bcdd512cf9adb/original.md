Extension: VK_EXT_image_compression_control

Arguments:

  * `image_subresource::_ImageSubresource`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkImageSubresource2EXT.html)

```julia
_ImageSubresource2EXT(
    image_subresource::Vulkan._ImageSubresource;
    next
) -> Vulkan._ImageSubresource2EXT

```
