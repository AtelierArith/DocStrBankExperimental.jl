拡張: VK*EXT*sample_locations

引数:

  * `attachment_initial_sample_locations::Vector{_AttachmentSampleLocationsEXT}`
  * `post_subpass_sample_locations::Vector{_SubpassSampleLocationsEXT}`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkRenderPassSampleLocationsBeginInfoEXT.html)

```julia
_RenderPassSampleLocationsBeginInfoEXT(
    attachment_initial_sample_locations::AbstractArray,
    post_subpass_sample_locations::AbstractArray;
    next
) -> Vulkan._RenderPassSampleLocationsBeginInfoEXT

```
