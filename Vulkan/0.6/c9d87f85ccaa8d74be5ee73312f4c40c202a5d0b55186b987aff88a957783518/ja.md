中間ラッパー VkRenderPassBeginInfo。

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkRenderPassBeginInfo.html)

```julia
struct _RenderPassBeginInfo <: Vulkan.VulkanStruct{true}
```

  * `vks::VulkanCore.LibVulkan.VkRenderPassBeginInfo`
  * `deps::Vector{Any}`
  * `render_pass::Vulkan.RenderPass`
  * `framebuffer::Vulkan.Framebuffer`
