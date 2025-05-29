拡張: VK*KHR*fragment*shading*rate

引数:

  * `shading_rate_attachment_texel_size::_Extent2D`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `fragment_shading_rate_attachment::_AttachmentReference2`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkFragmentShadingRateAttachmentInfoKHR.html)

```julia
_FragmentShadingRateAttachmentInfoKHR(
    shading_rate_attachment_texel_size::Vulkan._Extent2D;
    next,
    fragment_shading_rate_attachment
) -> Vulkan._FragmentShadingRateAttachmentInfoKHR

```
