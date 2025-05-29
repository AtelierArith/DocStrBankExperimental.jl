VkVideoPictureResourceInfoKHRの高レベルラッパー。

拡張: VK*KHR*video_queue

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkVideoPictureResourceInfoKHR.html)

```julia
struct VideoPictureResourceInfoKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `coded_offset::Vulkan.Offset2D`
  * `coded_extent::Vulkan.Extent2D`
  * `base_array_layer::UInt32`
  * `image_view_binding::Vulkan.ImageView`
