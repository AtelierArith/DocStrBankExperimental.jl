High-level wrapper for VkRenderPassSampleLocationsBeginInfoEXT.

Extension: VK_EXT_sample_locations

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkRenderPassSampleLocationsBeginInfoEXT.html)

```julia
struct RenderPassSampleLocationsBeginInfoEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `attachment_initial_sample_locations::Vector{Vulkan.AttachmentSampleLocationsEXT}`
  * `post_subpass_sample_locations::Vector{Vulkan.SubpassSampleLocationsEXT}`
