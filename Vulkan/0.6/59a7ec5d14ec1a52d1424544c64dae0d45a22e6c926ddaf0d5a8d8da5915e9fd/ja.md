拡張: VK*KHR*fragment*shading*rate

引数:

  * `shading_rate_attachment_texel_size::Extent2D`
  * `next::Any`: デフォルトは `C_NULL`
  * `fragment_shading_rate_attachment::AttachmentReference2`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkFragmentShadingRateAttachmentInfoKHR.html)

```julia
FragmentShadingRateAttachmentInfoKHR(
    shading_rate_attachment_texel_size::Vulkan.Extent2D;
    next,
    fragment_shading_rate_attachment
) -> Vulkan.FragmentShadingRateAttachmentInfoKHR

```
