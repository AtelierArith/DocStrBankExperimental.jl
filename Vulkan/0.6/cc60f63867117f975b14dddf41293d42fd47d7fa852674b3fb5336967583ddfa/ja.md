VkCommandBufferSubmitInfoの中間ラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCommandBufferSubmitInfo.html)

```julia
struct _CommandBufferSubmitInfo <: Vulkan.VulkanStruct{true}
```

  * `vks::VulkanCore.LibVulkan.VkCommandBufferSubmitInfo`
  * `deps::Vector{Any}`
  * `command_buffer::Vulkan.CommandBuffer`
