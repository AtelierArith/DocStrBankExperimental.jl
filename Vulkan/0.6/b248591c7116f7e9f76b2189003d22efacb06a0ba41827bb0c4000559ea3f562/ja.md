VkDebugMarkerMarkerInfoEXTの高レベルラッパー。

拡張: VK*EXT*debug_marker

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDebugMarkerMarkerInfoEXT.html)

```julia
struct DebugMarkerMarkerInfoEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `marker_name::String`
  * `color::NTuple{4, Float32}`
