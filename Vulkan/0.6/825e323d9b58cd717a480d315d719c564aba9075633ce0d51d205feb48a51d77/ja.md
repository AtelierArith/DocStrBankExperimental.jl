引数:

  * `stages::Vector{_PipelineShaderStageCreateInfo}`
  * `rasterization_state::_PipelineRasterizationStateCreateInfo`
  * `layout::PipelineLayout`
  * `subpass::UInt32`
  * `base_pipeline_index::Int32`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `flags::PipelineCreateFlag`: デフォルトは `0`
  * `vertex_input_state::_PipelineVertexInputStateCreateInfo`: デフォルトは `C_NULL`
  * `input_assembly_state::_PipelineInputAssemblyStateCreateInfo`: デフォルトは `C_NULL`
  * `tessellation_state::_PipelineTessellationStateCreateInfo`: デフォルトは `C_NULL`
  * `viewport_state::_PipelineViewportStateCreateInfo`: デフォルトは `C_NULL`
  * `multisample_state::_PipelineMultisampleStateCreateInfo`: デフォルトは `C_NULL`
  * `depth_stencil_state::_PipelineDepthStencilStateCreateInfo`: デフォルトは `C_NULL`
  * `color_blend_state::_PipelineColorBlendStateCreateInfo`: デフォルトは `C_NULL`
  * `dynamic_state::_PipelineDynamicStateCreateInfo`: デフォルトは `C_NULL`
  * `render_pass::RenderPass`: デフォルトは `C_NULL`
  * `base_pipeline_handle::Pipeline`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkGraphicsPipelineCreateInfo.html)

```julia
_GraphicsPipelineCreateInfo(
    stages::AbstractArray,
    rasterization_state::Vulkan._PipelineRasterizationStateCreateInfo,
    layout,
    subpass::Integer,
    base_pipeline_index::Integer;
    next,
    flags,
    vertex_input_state,
    input_assembly_state,
    tessellation_state,
    viewport_state,
    multisample_state,
    depth_stencil_state,
    color_blend_state,
    dynamic_state,
    render_pass,
    base_pipeline_handle
) -> Vulkan._GraphicsPipelineCreateInfo

```
