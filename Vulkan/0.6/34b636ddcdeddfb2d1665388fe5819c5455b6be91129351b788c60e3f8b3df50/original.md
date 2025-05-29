High-level wrapper for VkGraphicsShaderGroupCreateInfoNV.

Extension: VK_NV_device_generated_commands

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkGraphicsShaderGroupCreateInfoNV.html)

```julia
struct GraphicsShaderGroupCreateInfoNV <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `stages::Vector{Vulkan.PipelineShaderStageCreateInfo}`
  * `vertex_input_state::Union{Ptr{Nothing}, Vulkan.PipelineVertexInputStateCreateInfo}`
  * `tessellation_state::Union{Ptr{Nothing}, Vulkan.PipelineTessellationStateCreateInfo}`
