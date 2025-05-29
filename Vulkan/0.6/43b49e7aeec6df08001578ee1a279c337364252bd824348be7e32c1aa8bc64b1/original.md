High-level wrapper for VkDebugUtilsMessengerCreateInfoEXT.

Extension: VK_EXT_debug_utils

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDebugUtilsMessengerCreateInfoEXT.html)

```julia
struct DebugUtilsMessengerCreateInfoEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `flags::UInt32`
  * `message_severity::Vulkan.DebugUtilsMessageSeverityFlagEXT`
  * `message_type::Vulkan.DebugUtilsMessageTypeFlagEXT`
  * `pfn_user_callback::Union{Ptr{Nothing}, Base.CFunction}`
  * `user_data::Ptr{Nothing}`
