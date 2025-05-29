Arguments:

  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `flags::UInt32`: defaults to `0`
  * `viewports::Vector{_Viewport}`: defaults to `C_NULL`
  * `scissors::Vector{_Rect2D}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineViewportStateCreateInfo.html)

```julia
_PipelineViewportStateCreateInfo(
;
    next,
    flags,
    viewports,
    scissors
) -> Vulkan._PipelineViewportStateCreateInfo

```
