VkDebugMarkerObjectNameInfoEXTの高レベルラッパー。

拡張: VK*EXT*debug_marker

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDebugMarkerObjectNameInfoEXT.html)

```julia
struct DebugMarkerObjectNameInfoEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `object_type::Vulkan.DebugReportObjectTypeEXT`
  * `object::UInt64`
  * `object_name::String`
