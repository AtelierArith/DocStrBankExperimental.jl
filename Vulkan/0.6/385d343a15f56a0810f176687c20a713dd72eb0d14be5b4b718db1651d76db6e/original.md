Arguments:

  * `src_subresource::ImageSubresourceLayers`
  * `src_offsets::NTuple{2, Offset3D}`
  * `dst_subresource::ImageSubresourceLayers`
  * `dst_offsets::NTuple{2, Offset3D}`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkImageBlit2.html)

```julia
ImageBlit2(
    src_subresource::Vulkan.ImageSubresourceLayers,
    src_offsets::Tuple{Vulkan.Offset3D, Vulkan.Offset3D},
    dst_subresource::Vulkan.ImageSubresourceLayers,
    dst_offsets::Tuple{Vulkan.Offset3D, Vulkan.Offset3D};
    next
) -> Vulkan.ImageBlit2

```
