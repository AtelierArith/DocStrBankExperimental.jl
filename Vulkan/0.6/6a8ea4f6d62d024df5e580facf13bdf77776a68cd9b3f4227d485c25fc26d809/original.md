Extension: VK_KHR_video_decode_h265

Arguments:

  * `std_vp_ss::Vector{StdVideoH265VideoParameterSet}`
  * `std_sp_ss::Vector{StdVideoH265SequenceParameterSet}`
  * `std_pp_ss::Vector{StdVideoH265PictureParameterSet}`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkVideoDecodeH265SessionParametersAddInfoKHR.html)

```julia
VideoDecodeH265SessionParametersAddInfoKHR(
    std_vp_ss::AbstractArray,
    std_sp_ss::AbstractArray,
    std_pp_ss::AbstractArray;
    next
) -> Vulkan.VideoDecodeH265SessionParametersAddInfoKHR

```
