High-level wrapper for VkVideoDecodeH264PictureInfoKHR.

Extension: VK_KHR_video_decode_h264

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkVideoDecodeH264PictureInfoKHR.html)

```julia
struct VideoDecodeH264PictureInfoKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `std_picture_info::VulkanCore.LibVulkan.StdVideoDecodeH264PictureInfo`
  * `slice_offsets::Vector{UInt32}`
