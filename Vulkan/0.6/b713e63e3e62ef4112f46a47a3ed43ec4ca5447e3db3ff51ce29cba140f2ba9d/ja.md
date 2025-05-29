VkDebugReportCallbackCreateInfoEXTの高レベルラッパー。

拡張: VK*EXT*debug_report

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDebugReportCallbackCreateInfoEXT.html)

```julia
struct DebugReportCallbackCreateInfoEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `flags::Vulkan.DebugReportFlagEXT`
  * `pfn_callback::Union{Ptr{Nothing}, Base.CFunction}`
  * `user_data::Ptr{Nothing}`
