拡張機能: VK*KHR*video*decode*h265

引数:

  * `std_picture_info::StdVideoDecodeH265PictureInfo`
  * `slice_segment_offsets::Vector{UInt32}`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkVideoDecodeH265PictureInfoKHR.html)

```julia
VideoDecodeH265PictureInfoKHR(
    std_picture_info::VulkanCore.LibVulkan.StdVideoDecodeH265PictureInfo,
    slice_segment_offsets::AbstractArray;
    next
) -> Vulkan.VideoDecodeH265PictureInfoKHR

```
