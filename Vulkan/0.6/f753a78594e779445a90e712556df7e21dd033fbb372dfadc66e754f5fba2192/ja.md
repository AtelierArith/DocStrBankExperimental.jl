拡張: VK*KHR*video*decode*h265

引数:

  * `std_profile_idc::StdVideoH265ProfileIdc`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkVideoDecodeH265ProfileInfoKHR.html)

```julia
_VideoDecodeH265ProfileInfoKHR(
    std_profile_idc::VulkanCore.LibVulkan.StdVideoH265ProfileIdc;
    next
) -> Vulkan._VideoDecodeH265ProfileInfoKHR

```
