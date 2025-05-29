Arguments:

  * `next::Any`: defaults to `C_NULL`
  * `flags::UInt32`: defaults to `0`
  * `viewports::Vector{Viewport}`: defaults to `C_NULL`
  * `scissors::Vector{Rect2D}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineViewportStateCreateInfo.html)

```julia
PipelineViewportStateCreateInfo(
;
    next,
    flags,
    viewports,
    scissors
) -> Vulkan.PipelineViewportStateCreateInfo

```
