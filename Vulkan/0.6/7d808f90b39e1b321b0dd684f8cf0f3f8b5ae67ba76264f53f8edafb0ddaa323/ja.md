VkDebugMarkerObjectTagInfoEXTの高レベルラッパー。

拡張: VK*EXT*debug_marker

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDebugMarkerObjectTagInfoEXT.html)

```julia
struct DebugMarkerObjectTagInfoEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `object_type::Vulkan.DebugReportObjectTypeEXT`
  * `object::UInt64`
  * `tag_name::UInt64`
  * `tag_size::UInt64`
  * `tag::Ptr{Nothing}`
