拡張: VK*KHR*video*decode*h264

引数:

  * `std_sp_ss::Vector{StdVideoH264SequenceParameterSet}`
  * `std_pp_ss::Vector{StdVideoH264PictureParameterSet}`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkVideoDecodeH264SessionParametersAddInfoKHR.html)

```julia
VideoDecodeH264SessionParametersAddInfoKHR(
    std_sp_ss::AbstractArray,
    std_pp_ss::AbstractArray;
    next
) -> Vulkan.VideoDecodeH264SessionParametersAddInfoKHR

```
