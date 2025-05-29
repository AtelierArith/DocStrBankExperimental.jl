Extension: VK_EXT_discard_rectangles

Arguments:

  * `discard_rectangle_mode::DiscardRectangleModeEXT`
  * `discard_rectangles::Vector{Rect2D}`
  * `next::Any`: defaults to `C_NULL`
  * `flags::UInt32`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineDiscardRectangleStateCreateInfoEXT.html)

```julia
PipelineDiscardRectangleStateCreateInfoEXT(
    discard_rectangle_mode::Vulkan.DiscardRectangleModeEXT,
    discard_rectangles::AbstractArray;
    next,
    flags
) -> Vulkan.PipelineDiscardRectangleStateCreateInfoEXT

```
