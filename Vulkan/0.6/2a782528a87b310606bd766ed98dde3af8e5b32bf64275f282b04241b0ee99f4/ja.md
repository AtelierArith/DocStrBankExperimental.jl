拡張: VK*NV*device*generated*commands

引数:

  * `stages::Vector{PipelineShaderStageCreateInfo}`
  * `next::Any`: デフォルトは `C_NULL`
  * `vertex_input_state::PipelineVertexInputStateCreateInfo`: デフォルトは `C_NULL`
  * `tessellation_state::PipelineTessellationStateCreateInfo`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkGraphicsShaderGroupCreateInfoNV.html)

```julia
GraphicsShaderGroupCreateInfoNV(
    stages::AbstractArray;
    next,
    vertex_input_state,
    tessellation_state
) -> Vulkan.GraphicsShaderGroupCreateInfoNV

```
