拡張: VK*KHR*video*decode*h264

引数:

  * `max_std_sps_count::UInt32`
  * `max_std_pps_count::UInt32`
  * `next::Any`: デフォルトは `C_NULL`
  * `parameters_add_info::VideoDecodeH264SessionParametersAddInfoKHR`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkVideoDecodeH264SessionParametersCreateInfoKHR.html)

```julia
VideoDecodeH264SessionParametersCreateInfoKHR(
    max_std_sps_count::Integer,
    max_std_pps_count::Integer;
    next,
    parameters_add_info
) -> Vulkan.VideoDecodeH264SessionParametersCreateInfoKHR

```
