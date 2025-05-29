Extension: VK_KHR_fragment_shading_rate

Arguments:

  * `shading_rate_attachment_texel_size::Extent2D`
  * `next::Any`: defaults to `C_NULL`
  * `fragment_shading_rate_attachment::AttachmentReference2`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkFragmentShadingRateAttachmentInfoKHR.html)

```julia
FragmentShadingRateAttachmentInfoKHR(
    shading_rate_attachment_texel_size::Vulkan.Extent2D;
    next,
    fragment_shading_rate_attachment
) -> Vulkan.FragmentShadingRateAttachmentInfoKHR

```
