引数:

  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `flags::UInt32`: デフォルトは `0`
  * `viewports::Vector{_Viewport}`: デフォルトは `C_NULL`
  * `scissors::Vector{_Rect2D}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineViewportStateCreateInfo.html)

```julia
_PipelineViewportStateCreateInfo(
;
    next,
    flags,
    viewports,
    scissors
) -> Vulkan._PipelineViewportStateCreateInfo

```
