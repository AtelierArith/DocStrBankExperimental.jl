拡張: VK*EXT*transform_feedback

引数:

  * `rasterization_stream::UInt32`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `flags::UInt32`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineRasterizationStateStreamCreateInfoEXT.html)

```julia
_PipelineRasterizationStateStreamCreateInfoEXT(
    rasterization_stream::Integer;
    next,
    flags
) -> Vulkan._PipelineRasterizationStateStreamCreateInfoEXT

```
