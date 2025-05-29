拡張: VK*EXT*sample_locations

引数:

  * `attachment_initial_sample_locations::Vector{AttachmentSampleLocationsEXT}`
  * `post_subpass_sample_locations::Vector{SubpassSampleLocationsEXT}`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkRenderPassSampleLocationsBeginInfoEXT.html)

```julia
RenderPassSampleLocationsBeginInfoEXT(
    attachment_initial_sample_locations::AbstractArray,
    post_subpass_sample_locations::AbstractArray;
    next
) -> Vulkan.RenderPassSampleLocationsBeginInfoEXT

```
