引数:

  * `stages::Vector{PipelineShaderStageCreateInfo}`
  * `rasterization_state::PipelineRasterizationStateCreateInfo`
  * `layout::PipelineLayout`
  * `subpass::UInt32`
  * `base_pipeline_index::Int32`
  * `next::Any`: デフォルトは `C_NULL`
  * `flags::PipelineCreateFlag`: デフォルトは `0`
  * `vertex_input_state::PipelineVertexInputStateCreateInfo`: デフォルトは `C_NULL`
  * `input_assembly_state::PipelineInputAssemblyStateCreateInfo`: デフォルトは `C_NULL`
  * `tessellation_state::PipelineTessellationStateCreateInfo`: デフォルトは `C_NULL`
  * `viewport_state::PipelineViewportStateCreateInfo`: デフォルトは `C_NULL`
  * `multisample_state::PipelineMultisampleStateCreateInfo`: デフォルトは `C_NULL`
  * `depth_stencil_state::PipelineDepthStencilStateCreateInfo`: デフォルトは `C_NULL`
  * `color_blend_state::PipelineColorBlendStateCreateInfo`: デフォルトは `C_NULL`
  * `dynamic_state::PipelineDynamicStateCreateInfo`: デフォルトは `C_NULL`
  * `render_pass::RenderPass`: デフォルトは `C_NULL`
  * `base_pipeline_handle::Pipeline`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkGraphicsPipelineCreateInfo.html)

```julia
GraphicsPipelineCreateInfo(
    stages::AbstractArray,
    rasterization_state::Vulkan.PipelineRasterizationStateCreateInfo,
    layout::Vulkan.PipelineLayout,
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
) -> Vulkan.GraphicsPipelineCreateInfo

```
