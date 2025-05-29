拡張機能: VK*KHR*video*decode*h264

引数:

  * `std_profile_idc::StdVideoH264ProfileIdc`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `picture_layout::VideoDecodeH264PictureLayoutFlagKHR`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkVideoDecodeH264ProfileInfoKHR.html)

```julia
_VideoDecodeH264ProfileInfoKHR(
    std_profile_idc::VulkanCore.LibVulkan.StdVideoH264ProfileIdc;
    next,
    picture_layout
)

```
