VkVideoDecodeH265SessionParametersCreateInfoKHRの高レベルラッパー。

拡張: VK*KHR*video*decode*h265

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkVideoDecodeH265SessionParametersCreateInfoKHR.html)

```julia
struct VideoDecodeH265SessionParametersCreateInfoKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `max_std_vps_count::UInt32`
  * `max_std_sps_count::UInt32`
  * `max_std_pps_count::UInt32`
  * `parameters_add_info::Union{Ptr{Nothing}, Vulkan.VideoDecodeH265SessionParametersAddInfoKHR}`
