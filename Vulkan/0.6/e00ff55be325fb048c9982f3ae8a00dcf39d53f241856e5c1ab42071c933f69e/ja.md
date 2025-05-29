VkRenderPassSampleLocationsBeginInfoEXTの高レベルラッパー。

拡張: VK*EXT*sample_locations

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkRenderPassSampleLocationsBeginInfoEXT.html)

```julia
struct RenderPassSampleLocationsBeginInfoEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `attachment_initial_sample_locations::Vector{Vulkan.AttachmentSampleLocationsEXT}`
  * `post_subpass_sample_locations::Vector{Vulkan.SubpassSampleLocationsEXT}`
