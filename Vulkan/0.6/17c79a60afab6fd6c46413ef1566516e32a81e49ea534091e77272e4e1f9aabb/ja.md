VkVideoDecodeH264CapabilitiesKHRの高レベルラッパー。

拡張: VK*KHR*video*decode*h264

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkVideoDecodeH264CapabilitiesKHR.html)

```julia
struct VideoDecodeH264CapabilitiesKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `max_level_idc::VulkanCore.LibVulkan.StdVideoH264LevelIdc`
  * `field_offset_granularity::Vulkan.Offset2D`
