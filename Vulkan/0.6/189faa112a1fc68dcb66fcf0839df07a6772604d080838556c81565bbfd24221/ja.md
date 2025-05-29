中間ラッパー VkGraphicsPipelineCreateInfo。

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkGraphicsPipelineCreateInfo.html)

```julia
struct _GraphicsPipelineCreateInfo <: Vulkan.VulkanStruct{true}
```

  * `vks::VulkanCore.LibVulkan.VkGraphicsPipelineCreateInfo`
  * `deps::Vector{Any}`
  * `layout::Union{Ptr{Nothing}, Vulkan.PipelineLayout}`
  * `render_pass::Union{Ptr{Nothing}, Vulkan.RenderPass}`
  * `base_pipeline_handle::Union{Ptr{Nothing}, Vulkan.Pipeline}`
