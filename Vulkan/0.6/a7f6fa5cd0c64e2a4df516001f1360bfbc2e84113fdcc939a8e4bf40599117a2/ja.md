VkGraphicsPipelineCreateInfoの高レベルラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkGraphicsPipelineCreateInfo.html)

```julia
struct GraphicsPipelineCreateInfo <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `flags::Vulkan.PipelineCreateFlag`
  * `stages::Union{Ptr{Nothing}, Vector{Vulkan.PipelineShaderStageCreateInfo}}`
  * `vertex_input_state::Union{Ptr{Nothing}, Vulkan.PipelineVertexInputStateCreateInfo}`
  * `input_assembly_state::Union{Ptr{Nothing}, Vulkan.PipelineInputAssemblyStateCreateInfo}`
  * `tessellation_state::Union{Ptr{Nothing}, Vulkan.PipelineTessellationStateCreateInfo}`
  * `viewport_state::Union{Ptr{Nothing}, Vulkan.PipelineViewportStateCreateInfo}`
  * `rasterization_state::Union{Ptr{Nothing}, Vulkan.PipelineRasterizationStateCreateInfo}`
  * `multisample_state::Union{Ptr{Nothing}, Vulkan.PipelineMultisampleStateCreateInfo}`
  * `depth_stencil_state::Union{Ptr{Nothing}, Vulkan.PipelineDepthStencilStateCreateInfo}`
  * `color_blend_state::Union{Ptr{Nothing}, Vulkan.PipelineColorBlendStateCreateInfo}`
  * `dynamic_state::Union{Ptr{Nothing}, Vulkan.PipelineDynamicStateCreateInfo}`
  * `layout::Union{Ptr{Nothing}, Vulkan.PipelineLayout}`
  * `render_pass::Union{Ptr{Nothing}, Vulkan.RenderPass}`
  * `subpass::UInt32`
  * `base_pipeline_handle::Union{Ptr{Nothing}, Vulkan.Pipeline}`
  * `base_pipeline_index::Int32`
