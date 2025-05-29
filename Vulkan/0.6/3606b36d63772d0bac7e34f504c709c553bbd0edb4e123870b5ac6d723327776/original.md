High-level wrapper for VkCopyMicromapToMemoryInfoEXT.

Extension: VK_EXT_opacity_micromap

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCopyMicromapToMemoryInfoEXT.html)

```julia
struct CopyMicromapToMemoryInfoEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `src::Vulkan.MicromapEXT`
  * `dst::Vulkan.DeviceOrHostAddressKHR`
  * `mode::Vulkan.CopyMicromapModeEXT`
