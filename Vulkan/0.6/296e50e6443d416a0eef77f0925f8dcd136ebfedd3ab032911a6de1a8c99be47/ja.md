VkVideoFormatPropertiesKHRの高レベルラッパー。

拡張: VK*KHR*video_queue

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkVideoFormatPropertiesKHR.html)

```julia
struct VideoFormatPropertiesKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `format::Vulkan.Format`
  * `component_mapping::Vulkan.ComponentMapping`
  * `image_create_flags::Vulkan.ImageCreateFlag`
  * `image_type::Vulkan.ImageType`
  * `image_tiling::Vulkan.ImageTiling`
  * `image_usage_flags::Vulkan.ImageUsageFlag`
