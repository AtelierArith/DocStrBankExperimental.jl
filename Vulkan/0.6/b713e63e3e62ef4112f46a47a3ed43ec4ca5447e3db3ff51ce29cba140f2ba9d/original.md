High-level wrapper for VkDebugReportCallbackCreateInfoEXT.

Extension: VK_EXT_debug_report

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDebugReportCallbackCreateInfoEXT.html)

```julia
struct DebugReportCallbackCreateInfoEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `flags::Vulkan.DebugReportFlagEXT`
  * `pfn_callback::Union{Ptr{Nothing}, Base.CFunction}`
  * `user_data::Ptr{Nothing}`
