引数:

  * `max_extent::Extent3D`
  * `max_mip_levels::UInt32`
  * `max_array_layers::UInt32`
  * `max_resource_size::UInt64`
  * `sample_counts::SampleCountFlag`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkImageFormatProperties.html)

```julia
ImageFormatProperties(
    max_extent::Vulkan.Extent3D,
    max_mip_levels::Integer,
    max_array_layers::Integer,
    max_resource_size::Integer;
    sample_counts
) -> Vulkan.ImageFormatProperties

```
