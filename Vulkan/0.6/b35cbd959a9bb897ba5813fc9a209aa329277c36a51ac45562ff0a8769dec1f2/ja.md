拡張: VK*NV*device*generated*commands

引数:

  * `stages::Vector{_PipelineShaderStageCreateInfo}`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `vertex_input_state::_PipelineVertexInputStateCreateInfo`: デフォルトは `C_NULL`
  * `tessellation_state::_PipelineTessellationStateCreateInfo`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkGraphicsShaderGroupCreateInfoNV.html)

```julia
_GraphicsShaderGroupCreateInfoNV(
    stages::AbstractArray;
    next,
    vertex_input_state,
    tessellation_state
) -> Vulkan._GraphicsShaderGroupCreateInfoNV

```
