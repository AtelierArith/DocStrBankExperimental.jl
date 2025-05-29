Arguments:

  * `stages::Vector{PipelineShaderStageCreateInfo}`
  * `rasterization_state::PipelineRasterizationStateCreateInfo`
  * `layout::PipelineLayout`
  * `subpass::UInt32`
  * `base_pipeline_index::Int32`
  * `next::Any`: defaults to `C_NULL`
  * `flags::PipelineCreateFlag`: defaults to `0`
  * `vertex_input_state::PipelineVertexInputStateCreateInfo`: defaults to `C_NULL`
  * `input_assembly_state::PipelineInputAssemblyStateCreateInfo`: defaults to `C_NULL`
  * `tessellation_state::PipelineTessellationStateCreateInfo`: defaults to `C_NULL`
  * `viewport_state::PipelineViewportStateCreateInfo`: defaults to `C_NULL`
  * `multisample_state::PipelineMultisampleStateCreateInfo`: defaults to `C_NULL`
  * `depth_stencil_state::PipelineDepthStencilStateCreateInfo`: defaults to `C_NULL`
  * `color_blend_state::PipelineColorBlendStateCreateInfo`: defaults to `C_NULL`
  * `dynamic_state::PipelineDynamicStateCreateInfo`: defaults to `C_NULL`
  * `render_pass::RenderPass`: defaults to `C_NULL`
  * `base_pipeline_handle::Pipeline`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkGraphicsPipelineCreateInfo.html)

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
