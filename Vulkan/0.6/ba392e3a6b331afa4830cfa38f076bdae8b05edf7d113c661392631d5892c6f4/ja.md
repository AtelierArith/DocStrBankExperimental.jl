VkCopyMemoryToMicromapInfoEXTの高レベルラッパー。

拡張: VK*EXT*opacity_micromap

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCopyMemoryToMicromapInfoEXT.html)

```julia
struct CopyMemoryToMicromapInfoEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `src::Vulkan.DeviceOrHostAddressConstKHR`
  * `dst::Vulkan.MicromapEXT`
  * `mode::Vulkan.CopyMicromapModeEXT`
