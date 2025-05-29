Extension: VK_NV_device_generated_commands

Arguments:

  * `stages::Vector{PipelineShaderStageCreateInfo}`
  * `next::Any`: defaults to `C_NULL`
  * `vertex_input_state::PipelineVertexInputStateCreateInfo`: defaults to `C_NULL`
  * `tessellation_state::PipelineTessellationStateCreateInfo`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkGraphicsShaderGroupCreateInfoNV.html)

```julia
GraphicsShaderGroupCreateInfoNV(
    stages::AbstractArray;
    next,
    vertex_input_state,
    tessellation_state
) -> Vulkan.GraphicsShaderGroupCreateInfoNV

```
