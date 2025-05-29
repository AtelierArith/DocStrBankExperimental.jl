High-level wrapper for VkPipelineDiscardRectangleStateCreateInfoEXT.

Extension: VK_EXT_discard_rectangles

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineDiscardRectangleStateCreateInfoEXT.html)

```julia
struct PipelineDiscardRectangleStateCreateInfoEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `flags::UInt32`
  * `discard_rectangle_mode::Vulkan.DiscardRectangleModeEXT`
  * `discard_rectangles::Vector{Vulkan.Rect2D}`
