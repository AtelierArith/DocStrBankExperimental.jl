VkImageCompressionControlEXTの高レベルラッパー。

拡張: VK*EXT*image*compression*control

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkImageCompressionControlEXT.html)

```julia
struct ImageCompressionControlEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `flags::Vulkan.ImageCompressionFlagEXT`
  * `fixed_rate_flags::Vector{Vulkan.ImageCompressionFixedRateFlagEXT}`
