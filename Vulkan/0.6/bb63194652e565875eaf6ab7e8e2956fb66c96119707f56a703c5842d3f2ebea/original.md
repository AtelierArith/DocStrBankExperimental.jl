Extension: VK_KHR_video_decode_h264

Arguments:

  * `std_picture_info::StdVideoDecodeH264PictureInfo`
  * `slice_offsets::Vector{UInt32}`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkVideoDecodeH264PictureInfoKHR.html)

```julia
VideoDecodeH264PictureInfoKHR(
    std_picture_info::VulkanCore.LibVulkan.StdVideoDecodeH264PictureInfo,
    slice_offsets::AbstractArray;
    next
) -> Vulkan.VideoDecodeH264PictureInfoKHR

```
