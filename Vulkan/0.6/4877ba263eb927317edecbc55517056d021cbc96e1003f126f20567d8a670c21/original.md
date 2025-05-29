Arguments:

  * `src_subresource::_ImageSubresourceLayers`
  * `src_offsets::NTuple{2, _Offset3D}`
  * `dst_subresource::_ImageSubresourceLayers`
  * `dst_offsets::NTuple{2, _Offset3D}`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkImageBlit2.html)

```julia
_ImageBlit2(
    src_subresource::Vulkan._ImageSubresourceLayers,
    src_offsets::Tuple{Vulkan._Offset3D, Vulkan._Offset3D},
    dst_subresource::Vulkan._ImageSubresourceLayers,
    dst_offsets::Tuple{Vulkan._Offset3D, Vulkan._Offset3D};
    next
) -> Vulkan._ImageBlit2

```
