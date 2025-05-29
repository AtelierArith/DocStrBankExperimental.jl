拡張: VK*KHR*video*decode*h264

引数:

  * `std_picture_info::StdVideoDecodeH264PictureInfo`
  * `slice_offsets::Vector{UInt32}`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkVideoDecodeH264PictureInfoKHR.html)

```julia
_VideoDecodeH264PictureInfoKHR(
    std_picture_info::VulkanCore.LibVulkan.StdVideoDecodeH264PictureInfo,
    slice_offsets::AbstractArray;
    next
)

```
