VkRenderingAttachmentInfoの中間ラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkRenderingAttachmentInfo.html)

```julia
struct _RenderingAttachmentInfo <: Vulkan.VulkanStruct{true}
```

  * `vks::VulkanCore.LibVulkan.VkRenderingAttachmentInfo`
  * `deps::Vector{Any}`
  * `image_view::Union{Ptr{Nothing}, Vulkan.ImageView}`
  * `resolve_image_view::Union{Ptr{Nothing}, Vulkan.ImageView}`
