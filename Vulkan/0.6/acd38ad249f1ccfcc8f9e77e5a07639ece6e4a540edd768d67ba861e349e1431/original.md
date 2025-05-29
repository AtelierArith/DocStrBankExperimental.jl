Extension: VK_EXT_sample_locations

Arguments:

  * `attachment_initial_sample_locations::Vector{_AttachmentSampleLocationsEXT}`
  * `post_subpass_sample_locations::Vector{_SubpassSampleLocationsEXT}`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkRenderPassSampleLocationsBeginInfoEXT.html)

```julia
_RenderPassSampleLocationsBeginInfoEXT(
    attachment_initial_sample_locations::AbstractArray,
    post_subpass_sample_locations::AbstractArray;
    next
) -> Vulkan._RenderPassSampleLocationsBeginInfoEXT

```
