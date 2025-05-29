Extension: VK_KHR_video_decode_h264

Arguments:

  * `max_std_sps_count::UInt32`
  * `max_std_pps_count::UInt32`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `parameters_add_info::_VideoDecodeH264SessionParametersAddInfoKHR`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkVideoDecodeH264SessionParametersCreateInfoKHR.html)

```julia
_VideoDecodeH264SessionParametersCreateInfoKHR(
    max_std_sps_count::Integer,
    max_std_pps_count::Integer;
    next,
    parameters_add_info
) -> Vulkan._VideoDecodeH264SessionParametersCreateInfoKHR

```
