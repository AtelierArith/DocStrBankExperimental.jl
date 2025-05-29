High-level wrapper for VkGraphicsPipelineShaderGroupsCreateInfoNV.

Extension: VK_NV_device_generated_commands

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkGraphicsPipelineShaderGroupsCreateInfoNV.html)

```julia
struct GraphicsPipelineShaderGroupsCreateInfoNV <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `groups::Vector{Vulkan.GraphicsShaderGroupCreateInfoNV}`
  * `pipelines::Vector{Vulkan.Pipeline}`
