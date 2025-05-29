VkDebugUtilsObjectTagInfoEXTの高レベルラッパー。

拡張: VK*EXT*debug_utils

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDebugUtilsObjectTagInfoEXT.html)

```julia
struct DebugUtilsObjectTagInfoEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `object_type::Vulkan.ObjectType`
  * `object_handle::UInt64`
  * `tag_name::UInt64`
  * `tag_size::UInt64`
  * `tag::Ptr{Nothing}`
