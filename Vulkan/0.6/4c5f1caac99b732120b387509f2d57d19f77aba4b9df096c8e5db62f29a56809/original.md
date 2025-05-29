High-level wrapper for VkCommandBufferInheritanceInfo.

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCommandBufferInheritanceInfo.html)

```julia
struct CommandBufferInheritanceInfo <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `render_pass::Union{Ptr{Nothing}, Vulkan.RenderPass}`
  * `subpass::UInt32`
  * `framebuffer::Union{Ptr{Nothing}, Vulkan.Framebuffer}`
  * `occlusion_query_enable::Bool`
  * `query_flags::Vulkan.QueryControlFlag`
  * `pipeline_statistics::Vulkan.QueryPipelineStatisticFlag`
