VkImageCompressionPropertiesEXTの高レベルラッパー。

拡張: VK*EXT*image*compression*control

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkImageCompressionPropertiesEXT.html)

```julia
struct ImageCompressionPropertiesEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `image_compression_flags::Vulkan.ImageCompressionFlagEXT`
  * `image_compression_fixed_rate_flags::Vulkan.ImageCompressionFixedRateFlagEXT`
