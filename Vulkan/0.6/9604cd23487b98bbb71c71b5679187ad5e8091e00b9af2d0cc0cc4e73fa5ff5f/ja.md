引数:

  * `stage::_PipelineShaderStageCreateInfo`
  * `layout::PipelineLayout`
  * `base_pipeline_index::Int32`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `flags::PipelineCreateFlag`: デフォルトは `0`
  * `base_pipeline_handle::Pipeline`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkComputePipelineCreateInfo.html)

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
