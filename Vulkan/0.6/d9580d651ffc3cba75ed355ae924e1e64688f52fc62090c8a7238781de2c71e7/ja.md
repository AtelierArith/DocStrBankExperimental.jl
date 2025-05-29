VkVideoDecodeH265SessionParametersAddInfoKHRの高レベルラッパー。

拡張: VK*KHR*video*decode*h265

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkVideoDecodeH265SessionParametersAddInfoKHR.html)

```julia
struct VideoDecodeH265SessionParametersAddInfoKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `std_vp_ss::Vector{VulkanCore.LibVulkan.StdVideoH265VideoParameterSet}`
  * `std_sp_ss::Vector{VulkanCore.LibVulkan.StdVideoH265SequenceParameterSet}`
  * `std_pp_ss::Vector{VulkanCore.LibVulkan.StdVideoH265PictureParameterSet}`
