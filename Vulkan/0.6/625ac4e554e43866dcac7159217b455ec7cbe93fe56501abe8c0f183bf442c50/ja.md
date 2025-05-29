引数:

  * `next::Any`: デフォルトは `C_NULL`
  * `flags::UInt32`: デフォルトは `0`
  * `viewports::Vector{Viewport}`: デフォルトは `C_NULL`
  * `scissors::Vector{Rect2D}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineViewportStateCreateInfo.html)

```julia
PipelineViewportStateCreateInfo(
;
    next,
    flags,
    viewports,
    scissors
) -> Vulkan.PipelineViewportStateCreateInfo

```
