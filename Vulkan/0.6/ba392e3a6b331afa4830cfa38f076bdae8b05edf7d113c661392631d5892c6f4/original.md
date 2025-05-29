High-level wrapper for VkCopyMemoryToMicromapInfoEXT.

Extension: VK_EXT_opacity_micromap

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCopyMemoryToMicromapInfoEXT.html)

```julia
struct CopyMemoryToMicromapInfoEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `src::Vulkan.DeviceOrHostAddressConstKHR`
  * `dst::Vulkan.MicromapEXT`
  * `mode::Vulkan.CopyMicromapModeEXT`
