VkCopyMicromapInfoEXTの高レベルラッパー。

拡張: VK*EXT*opacity_micromap

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCopyMicromapInfoEXT.html)

```julia
struct CopyMicromapInfoEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `src::Vulkan.MicromapEXT`
  * `dst::Vulkan.MicromapEXT`
  * `mode::Vulkan.CopyMicromapModeEXT`
