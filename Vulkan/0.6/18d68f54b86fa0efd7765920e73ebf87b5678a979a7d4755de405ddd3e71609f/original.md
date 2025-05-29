High-level wrapper for VkImageCompressionControlEXT.

Extension: VK_EXT_image_compression_control

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkImageCompressionControlEXT.html)

```julia
struct ImageCompressionControlEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `flags::Vulkan.ImageCompressionFlagEXT`
  * `fixed_rate_flags::Vector{Vulkan.ImageCompressionFixedRateFlagEXT}`
