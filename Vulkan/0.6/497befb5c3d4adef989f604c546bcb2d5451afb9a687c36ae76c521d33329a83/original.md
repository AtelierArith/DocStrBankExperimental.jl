High-level wrapper for VkMicromapCreateInfoEXT.

Extension: VK_EXT_opacity_micromap

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkMicromapCreateInfoEXT.html)

```julia
struct MicromapCreateInfoEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `create_flags::Vulkan.MicromapCreateFlagEXT`
  * `buffer::Vulkan.Buffer`
  * `offset::UInt64`
  * `size::UInt64`
  * `type::Vulkan.MicromapTypeEXT`
  * `device_address::UInt64`
