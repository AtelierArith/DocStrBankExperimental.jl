VkVideoDecodeH265PictureInfoKHRの高レベルラッパー。

拡張: VK*KHR*video*decode*h265

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkVideoDecodeH265PictureInfoKHR.html)

```julia
struct VideoDecodeH265PictureInfoKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `std_picture_info::VulkanCore.LibVulkan.StdVideoDecodeH265PictureInfo`
  * `slice_segment_offsets::Vector{UInt32}`
