拡張: VK*EXT*image*compression*control

引数:

  * `image_subresource::_ImageSubresource`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkImageSubresource2EXT.html)

```julia
_ImageSubresource2EXT(
    image_subresource::Vulkan._ImageSubresource;
    next
) -> Vulkan._ImageSubresource2EXT

```
