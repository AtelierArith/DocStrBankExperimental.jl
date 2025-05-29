Arguments:

  * `image_granularity::_Extent3D`
  * `aspect_mask::ImageAspectFlag`: defaults to `0`
  * `flags::SparseImageFormatFlag`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSparseImageFormatProperties.html)

```julia
_SparseImageFormatProperties(
    image_granularity::Vulkan._Extent3D;
    aspect_mask,
    flags
) -> Vulkan._SparseImageFormatProperties

```
