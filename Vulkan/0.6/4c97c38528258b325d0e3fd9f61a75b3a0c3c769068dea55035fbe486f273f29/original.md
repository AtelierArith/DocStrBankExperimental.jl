Arguments:

  * `src_subresource::_ImageSubresourceLayers`
  * `src_offset::_Offset3D`
  * `dst_subresource::_ImageSubresourceLayers`
  * `dst_offset::_Offset3D`
  * `extent::_Extent3D`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkImageResolve.html)

```julia
_ImageResolve(
    src_subresource::Vulkan._ImageSubresourceLayers,
    src_offset::Vulkan._Offset3D,
    dst_subresource::Vulkan._ImageSubresourceLayers,
    dst_offset::Vulkan._Offset3D,
    extent::Vulkan._Extent3D
) -> Vulkan._ImageResolve

```
