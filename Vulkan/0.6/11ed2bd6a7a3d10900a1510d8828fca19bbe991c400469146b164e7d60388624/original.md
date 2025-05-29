High-level wrapper for VkVideoDecodeH264SessionParametersAddInfoKHR.

Extension: VK_KHR_video_decode_h264

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkVideoDecodeH264SessionParametersAddInfoKHR.html)

```julia
struct VideoDecodeH264SessionParametersAddInfoKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `std_sp_ss::Vector{VulkanCore.LibVulkan.StdVideoH264SequenceParameterSet}`
  * `std_pp_ss::Vector{VulkanCore.LibVulkan.StdVideoH264PictureParameterSet}`
