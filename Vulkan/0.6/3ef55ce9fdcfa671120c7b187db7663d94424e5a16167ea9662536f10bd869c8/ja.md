引数:

  * `src_subresource::_ImageSubresourceLayers`
  * `src_offset::_Offset3D`
  * `dst_subresource::_ImageSubresourceLayers`
  * `dst_offset::_Offset3D`
  * `extent::_Extent3D`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkImageResolve2.html)

```julia
_ImageResolve2(
    src_subresource::Vulkan._ImageSubresourceLayers,
    src_offset::Vulkan._Offset3D,
    dst_subresource::Vulkan._ImageSubresourceLayers,
    dst_offset::Vulkan._Offset3D,
    extent::Vulkan._Extent3D;
    next
) -> Vulkan._ImageResolve2

```
