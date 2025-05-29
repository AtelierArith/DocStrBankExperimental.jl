VkImageDrmFormatModifierExplicitCreateInfoEXTの高レベルラッパー。

拡張: VK*EXT*image*drm*format_modifier

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkImageDrmFormatModifierExplicitCreateInfoEXT.html)

```julia
struct ImageDrmFormatModifierExplicitCreateInfoEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `drm_format_modifier::UInt64`
  * `plane_layouts::Vector{Vulkan.SubresourceLayout}`
