VkVideoDecodeH264ProfileInfoKHRの高レベルラッパー。

拡張: VK*KHR*video*decode*h264

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkVideoDecodeH264ProfileInfoKHR.html)

```julia
struct VideoDecodeH264ProfileInfoKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `std_profile_idc::VulkanCore.LibVulkan.StdVideoH264ProfileIdc`
  * `picture_layout::Vulkan.VideoDecodeH264PictureLayoutFlagKHR`
