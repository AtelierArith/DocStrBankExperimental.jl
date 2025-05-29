VkVideoDecodeH264PictureInfoKHRの高レベルラッパー。

拡張: VK*KHR*video*decode*h264

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkVideoDecodeH264PictureInfoKHR.html)

```julia
struct VideoDecodeH264PictureInfoKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `std_picture_info::VulkanCore.LibVulkan.StdVideoDecodeH264PictureInfo`
  * `slice_offsets::Vector{UInt32}`
