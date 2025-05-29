拡張: VK*EXT*image*compression*control

引数:

  * `subresource_layout::_SubresourceLayout`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSubresourceLayout2EXT.html)

```julia
_SubresourceLayout2EXT(
    subresource_layout::Vulkan._SubresourceLayout;
    next
) -> Vulkan._SubresourceLayout2EXT

```
