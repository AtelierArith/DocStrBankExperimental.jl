High-level wrapper for VkDebugMarkerObjectNameInfoEXT.

Extension: VK_EXT_debug_marker

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDebugMarkerObjectNameInfoEXT.html)

```julia
struct DebugMarkerObjectNameInfoEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `object_type::Vulkan.DebugReportObjectTypeEXT`
  * `object::UInt64`
  * `object_name::String`
