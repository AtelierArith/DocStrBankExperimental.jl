拡張: VK*EXT*image*compression*control

引数:

  * `image_compression_flags::ImageCompressionFlagEXT`
  * `image_compression_fixed_rate_flags::ImageCompressionFixedRateFlagEXT`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkImageCompressionPropertiesEXT.html)

```julia
ImageCompressionPropertiesEXT(
    image_compression_flags::Vulkan.ImageCompressionFlagEXT,
    image_compression_fixed_rate_flags::Vulkan.ImageCompressionFixedRateFlagEXT;
    next
) -> Vulkan.ImageCompressionPropertiesEXT

```
