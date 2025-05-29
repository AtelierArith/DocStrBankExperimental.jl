High-level wrapper for VkVideoPictureResourceInfoKHR.

Extension: VK_KHR_video_queue

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkVideoPictureResourceInfoKHR.html)

```julia
struct VideoPictureResourceInfoKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `coded_offset::Vulkan.Offset2D`
  * `coded_extent::Vulkan.Extent2D`
  * `base_array_layer::UInt32`
  * `image_view_binding::Vulkan.ImageView`
