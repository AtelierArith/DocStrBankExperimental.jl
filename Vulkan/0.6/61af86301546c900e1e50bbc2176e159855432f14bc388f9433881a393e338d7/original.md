Extension: VK_EXT_image_compression_control

Arguments:

  * `image_compression_flags::ImageCompressionFlagEXT`
  * `image_compression_fixed_rate_flags::ImageCompressionFixedRateFlagEXT`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkImageCompressionPropertiesEXT.html)

```julia
ImageCompressionPropertiesEXT(
    image_compression_flags::Vulkan.ImageCompressionFlagEXT,
    image_compression_fixed_rate_flags::Vulkan.ImageCompressionFixedRateFlagEXT;
    next
) -> Vulkan.ImageCompressionPropertiesEXT

```
