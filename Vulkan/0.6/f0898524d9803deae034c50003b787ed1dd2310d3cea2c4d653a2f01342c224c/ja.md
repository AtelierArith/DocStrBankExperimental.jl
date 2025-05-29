VkVideoCapabilitiesKHRの高レベルラッパー。

拡張: VK*KHR*video_queue

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkVideoCapabilitiesKHR.html)

```julia
struct VideoCapabilitiesKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `flags::Vulkan.VideoCapabilityFlagKHR`
  * `min_bitstream_buffer_offset_alignment::UInt64`
  * `min_bitstream_buffer_size_alignment::UInt64`
  * `picture_access_granularity::Vulkan.Extent2D`
  * `min_coded_extent::Vulkan.Extent2D`
  * `max_coded_extent::Vulkan.Extent2D`
  * `max_dpb_slots::UInt32`
  * `max_active_reference_pictures::UInt32`
  * `std_header_version::Vulkan.ExtensionProperties`
