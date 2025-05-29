Extension: VK_KHR_video_decode_h264

Arguments:

  * `std_profile_idc::StdVideoH264ProfileIdc`
  * `next::Any`: defaults to `C_NULL`
  * `picture_layout::VideoDecodeH264PictureLayoutFlagKHR`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkVideoDecodeH264ProfileInfoKHR.html)

```julia
VideoDecodeH264ProfileInfoKHR(
    std_profile_idc::VulkanCore.LibVulkan.StdVideoH264ProfileIdc;
    next,
    picture_layout
) -> Vulkan.VideoDecodeH264ProfileInfoKHR

```
