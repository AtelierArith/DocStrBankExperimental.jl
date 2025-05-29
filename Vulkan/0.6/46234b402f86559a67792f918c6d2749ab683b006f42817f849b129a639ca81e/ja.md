中間ラッパー VkCommandBufferInheritanceInfo。

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCommandBufferInheritanceInfo.html)

```julia
struct _CommandBufferInheritanceInfo <: Vulkan.VulkanStruct{true}
```

  * `vks::VulkanCore.LibVulkan.VkCommandBufferInheritanceInfo`
  * `deps::Vector{Any}`
  * `render_pass::Union{Ptr{Nothing}, Vulkan.RenderPass}`
  * `framebuffer::Union{Ptr{Nothing}, Vulkan.Framebuffer}`
