VkValidationCacheCreateInfoEXTの高レベルラッパー。

拡張: VK*EXT*validation_cache

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkValidationCacheCreateInfoEXT.html)

```julia
struct ValidationCacheCreateInfoEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `flags::UInt32`
  * `initial_data_size::Union{Ptr{Nothing}, UInt64}`
  * `initial_data::Ptr{Nothing}`
