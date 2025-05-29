Extension: VK_KHR_video_decode_h265

Arguments:

  * `std_picture_info::StdVideoDecodeH265PictureInfo`
  * `slice_segment_offsets::Vector{UInt32}`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkVideoDecodeH265PictureInfoKHR.html)

```julia
_VideoDecodeH265PictureInfoKHR(
    std_picture_info::VulkanCore.LibVulkan.StdVideoDecodeH265PictureInfo,
    slice_segment_offsets::AbstractArray;
    next
)

```
