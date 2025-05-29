Extension: VK_EXT_discard_rectangles

Arguments:

  * `discard_rectangle_mode::DiscardRectangleModeEXT`
  * `discard_rectangles::Vector{_Rect2D}`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `flags::UInt32`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineDiscardRectangleStateCreateInfoEXT.html)

```julia
_PipelineDiscardRectangleStateCreateInfoEXT(
    discard_rectangle_mode::Vulkan.DiscardRectangleModeEXT,
    discard_rectangles::AbstractArray;
    next,
    flags
) -> Vulkan._PipelineDiscardRectangleStateCreateInfoEXT

```
