VkPhysicalDeviceSparseImageFormatInfo2の高レベルラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceSparseImageFormatInfo2.html)

```julia
struct PhysicalDeviceSparseImageFormatInfo2 <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `format::Vulkan.Format`
  * `type::Vulkan.ImageType`
  * `samples::Vulkan.SampleCountFlag`
  * `usage::Vulkan.ImageUsageFlag`
  * `tiling::Vulkan.ImageTiling`
