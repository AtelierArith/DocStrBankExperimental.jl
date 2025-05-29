引数:

  * `src_subresource::_ImageSubresourceLayers`
  * `src_offsets::NTuple{2, _Offset3D}`
  * `dst_subresource::_ImageSubresourceLayers`
  * `dst_offsets::NTuple{2, _Offset3D}`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkImageBlit.html)

```julia
_ImageBlit(
    src_subresource::Vulkan._ImageSubresourceLayers,
    src_offsets::Tuple{Vulkan._Offset3D, Vulkan._Offset3D},
    dst_subresource::Vulkan._ImageSubresourceLayers,
    dst_offsets::Tuple{Vulkan._Offset3D, Vulkan._Offset3D}
) -> Vulkan._ImageBlit

```
