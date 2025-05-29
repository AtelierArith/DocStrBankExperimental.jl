Extension: VK_KHR_video_decode_h264

Arguments:

  * `std_sp_ss::Vector{StdVideoH264SequenceParameterSet}`
  * `std_pp_ss::Vector{StdVideoH264PictureParameterSet}`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkVideoDecodeH264SessionParametersAddInfoKHR.html)

```julia
VideoDecodeH264SessionParametersAddInfoKHR(
    std_sp_ss::AbstractArray,
    std_pp_ss::AbstractArray;
    next
) -> Vulkan.VideoDecodeH264SessionParametersAddInfoKHR

```
