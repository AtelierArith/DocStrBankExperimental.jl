Extension: VK_KHR_fragment_shading_rate

Arguments:

  * `shading_rate_attachment_texel_size::_Extent2D`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `fragment_shading_rate_attachment::_AttachmentReference2`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkFragmentShadingRateAttachmentInfoKHR.html)

```julia
_FragmentShadingRateAttachmentInfoKHR(
    shading_rate_attachment_texel_size::Vulkan._Extent2D;
    next,
    fragment_shading_rate_attachment
) -> Vulkan._FragmentShadingRateAttachmentInfoKHR

```
