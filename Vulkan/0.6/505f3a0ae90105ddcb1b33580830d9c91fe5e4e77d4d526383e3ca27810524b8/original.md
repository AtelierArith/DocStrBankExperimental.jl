High-level wrapper for VkVideoDecodeH265PictureInfoKHR.

Extension: VK_KHR_video_decode_h265

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkVideoDecodeH265PictureInfoKHR.html)

```julia
struct VideoDecodeH265PictureInfoKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `std_picture_info::VulkanCore.LibVulkan.StdVideoDecodeH265PictureInfo`
  * `slice_segment_offsets::Vector{UInt32}`
