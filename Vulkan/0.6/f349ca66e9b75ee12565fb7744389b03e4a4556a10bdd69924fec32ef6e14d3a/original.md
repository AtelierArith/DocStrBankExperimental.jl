High-level wrapper for VkValidationCacheCreateInfoEXT.

Extension: VK_EXT_validation_cache

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkValidationCacheCreateInfoEXT.html)

```julia
struct ValidationCacheCreateInfoEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `flags::UInt32`
  * `initial_data_size::Union{Ptr{Nothing}, UInt64}`
  * `initial_data::Ptr{Nothing}`
