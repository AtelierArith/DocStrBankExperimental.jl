拡張機能: VK*KHR*video*decode*h265

引数:

  * `max_std_vps_count::UInt32`
  * `max_std_sps_count::UInt32`
  * `max_std_pps_count::UInt32`
  * `next::Any`: デフォルトは `C_NULL`
  * `parameters_add_info::VideoDecodeH265SessionParametersAddInfoKHR`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkVideoDecodeH265SessionParametersCreateInfoKHR.html)

```julia
VideoDecodeH265SessionParametersCreateInfoKHR(
    max_std_vps_count::Integer,
    max_std_sps_count::Integer,
    max_std_pps_count::Integer;
    next,
    parameters_add_info
) -> Vulkan.VideoDecodeH265SessionParametersCreateInfoKHR

```
