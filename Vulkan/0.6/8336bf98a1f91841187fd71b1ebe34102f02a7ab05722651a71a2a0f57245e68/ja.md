引数:

  * `image_granularity::Extent3D`
  * `aspect_mask::ImageAspectFlag`: デフォルトは `0`
  * `flags::SparseImageFormatFlag`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSparseImageFormatProperties.html)

```julia
SparseImageFormatProperties(
    image_granularity::Vulkan.Extent3D;
    aspect_mask,
    flags
) -> Vulkan.SparseImageFormatProperties

```
