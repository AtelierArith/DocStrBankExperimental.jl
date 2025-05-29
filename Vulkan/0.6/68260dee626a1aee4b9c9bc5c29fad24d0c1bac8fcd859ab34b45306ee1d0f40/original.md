High-level wrapper for VkVideoDecodeH264SessionParametersCreateInfoKHR.

Extension: VK_KHR_video_decode_h264

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkVideoDecodeH264SessionParametersCreateInfoKHR.html)

```julia
struct VideoDecodeH264SessionParametersCreateInfoKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `max_std_sps_count::UInt32`
  * `max_std_pps_count::UInt32`
  * `parameters_add_info::Union{Ptr{Nothing}, Vulkan.VideoDecodeH264SessionParametersAddInfoKHR}`
