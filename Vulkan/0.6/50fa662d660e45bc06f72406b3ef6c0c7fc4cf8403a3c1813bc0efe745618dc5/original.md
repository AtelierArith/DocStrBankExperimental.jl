Extension: VK_EXT_transform_feedback

Arguments:

  * `rasterization_stream::UInt32`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `flags::UInt32`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineRasterizationStateStreamCreateInfoEXT.html)

```julia
_PipelineRasterizationStateStreamCreateInfoEXT(
    rasterization_stream::Integer;
    next,
    flags
) -> Vulkan._PipelineRasterizationStateStreamCreateInfoEXT

```
