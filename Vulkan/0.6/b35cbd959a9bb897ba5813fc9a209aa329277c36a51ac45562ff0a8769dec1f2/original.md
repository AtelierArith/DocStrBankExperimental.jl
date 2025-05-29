Extension: VK_NV_device_generated_commands

Arguments:

  * `stages::Vector{_PipelineShaderStageCreateInfo}`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `vertex_input_state::_PipelineVertexInputStateCreateInfo`: defaults to `C_NULL`
  * `tessellation_state::_PipelineTessellationStateCreateInfo`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkGraphicsShaderGroupCreateInfoNV.html)

```julia
_GraphicsShaderGroupCreateInfoNV(
    stages::AbstractArray;
    next,
    vertex_input_state,
    tessellation_state
) -> Vulkan._GraphicsShaderGroupCreateInfoNV

```
