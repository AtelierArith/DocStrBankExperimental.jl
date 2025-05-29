VkVideoSessionCreateInfoKHRの高レベルラッパー。

拡張: VK*KHR*video_queue

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkVideoSessionCreateInfoKHR.html)

```julia
struct VideoSessionCreateInfoKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `queue_family_index::UInt32`
  * `flags::Vulkan.VideoSessionCreateFlagKHR`
  * `video_profile::Vulkan.VideoProfileInfoKHR`
  * `picture_format::Vulkan.Format`
  * `max_coded_extent::Vulkan.Extent2D`
  * `reference_picture_format::Vulkan.Format`
  * `max_dpb_slots::UInt32`
  * `max_active_reference_pictures::UInt32`
  * `std_header_version::Vulkan.ExtensionProperties`
