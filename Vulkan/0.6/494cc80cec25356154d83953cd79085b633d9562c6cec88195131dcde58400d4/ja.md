VkDebugUtilsLabelEXTの高レベルラッパー。

拡張: VK*EXT*debug_utils

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDebugUtilsLabelEXT.html)

```julia
struct DebugUtilsLabelEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `label_name::String`
  * `color::NTuple{4, Float32}`
