VkPhysicalDeviceImageDrmFormatModifierInfoEXTの高レベルラッパー。

拡張: VK*EXT*image*drm*format_modifier

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceImageDrmFormatModifierInfoEXT.html)

```julia
struct PhysicalDeviceImageDrmFormatModifierInfoEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `drm_format_modifier::UInt64`
  * `sharing_mode::Vulkan.SharingMode`
  * `queue_family_indices::Vector{UInt32}`
