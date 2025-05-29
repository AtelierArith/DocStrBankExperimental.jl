拡張: VK*EXT*transform_feedback

引数:

  * `rasterization_stream::UInt32`
  * `next::Any`: デフォルトは `C_NULL`
  * `flags::UInt32`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineRasterizationStateStreamCreateInfoEXT.html)

```julia
PipelineRasterizationStateStreamCreateInfoEXT(
    rasterization_stream::Integer;
    next,
    flags
) -> Vulkan.PipelineRasterizationStateStreamCreateInfoEXT

```
