VkDebugUtilsObjectNameInfoEXTの高レベルラッパー。

拡張: VK*EXT*debug_utils

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDebugUtilsObjectNameInfoEXT.html)

```julia
struct DebugUtilsObjectNameInfoEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `object_type::Vulkan.ObjectType`
  * `object_handle::UInt64`
  * `object_name::String`
