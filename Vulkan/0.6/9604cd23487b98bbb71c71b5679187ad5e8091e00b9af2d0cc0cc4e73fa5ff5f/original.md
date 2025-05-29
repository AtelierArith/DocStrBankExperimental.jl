Arguments:

  * `stage::_PipelineShaderStageCreateInfo`
  * `layout::PipelineLayout`
  * `base_pipeline_index::Int32`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `flags::PipelineCreateFlag`: defaults to `0`
  * `base_pipeline_handle::Pipeline`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkComputePipelineCreateInfo.html)

```julia
_ComputePipelineCreateInfo(
    stage::Vulkan._PipelineShaderStageCreateInfo,
    layout,
    base_pipeline_index::Integer;
    next,
    flags,
    base_pipeline_handle
) -> Vulkan._ComputePipelineCreateInfo

```
