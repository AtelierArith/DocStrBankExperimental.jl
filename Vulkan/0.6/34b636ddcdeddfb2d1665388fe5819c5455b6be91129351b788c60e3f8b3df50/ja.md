VkGraphicsShaderGroupCreateInfoNVの高レベルラッパー。

拡張: VK*NV*device*generated*commands

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkGraphicsShaderGroupCreateInfoNV.html)

```julia
struct GraphicsShaderGroupCreateInfoNV <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `stages::Vector{Vulkan.PipelineShaderStageCreateInfo}`
  * `vertex_input_state::Union{Ptr{Nothing}, Vulkan.PipelineVertexInputStateCreateInfo}`
  * `tessellation_state::Union{Ptr{Nothing}, Vulkan.PipelineTessellationStateCreateInfo}`
