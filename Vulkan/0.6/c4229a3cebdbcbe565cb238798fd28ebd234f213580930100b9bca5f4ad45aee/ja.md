拡張: VK*EXT*discard_rectangles

引数:

  * `discard_rectangle_mode::DiscardRectangleModeEXT`
  * `discard_rectangles::Vector{_Rect2D}`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `flags::UInt32`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineDiscardRectangleStateCreateInfoEXT.html)

```julia
_PipelineDiscardRectangleStateCreateInfoEXT(
    discard_rectangle_mode::Vulkan.DiscardRectangleModeEXT,
    discard_rectangles::AbstractArray;
    next,
    flags
) -> Vulkan._PipelineDiscardRectangleStateCreateInfoEXT

```
