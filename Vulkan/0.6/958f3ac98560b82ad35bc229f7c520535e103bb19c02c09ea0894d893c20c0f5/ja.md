VkPhysicalDeviceImageFormatInfo2の高レベルラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceImageFormatInfo2.html)

```julia
struct PhysicalDeviceImageFormatInfo2 <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `format::Vulkan.Format`
  * `type::Vulkan.ImageType`
  * `tiling::Vulkan.ImageTiling`
  * `usage::Vulkan.ImageUsageFlag`
  * `flags::Vulkan.ImageCreateFlag`
