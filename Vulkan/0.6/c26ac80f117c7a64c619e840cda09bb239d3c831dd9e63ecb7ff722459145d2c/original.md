High-level wrapper for VkDebugUtilsObjectNameInfoEXT.

Extension: VK_EXT_debug_utils

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDebugUtilsObjectNameInfoEXT.html)

```julia
struct DebugUtilsObjectNameInfoEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `object_type::Vulkan.ObjectType`
  * `object_handle::UInt64`
  * `object_name::String`
