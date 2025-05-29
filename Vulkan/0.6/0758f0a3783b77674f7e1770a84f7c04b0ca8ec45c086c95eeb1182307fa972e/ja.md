VkPipelineDiscardRectangleStateCreateInfoEXTの高レベルラッパー。

拡張: VK*EXT*discard_rectangles

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineDiscardRectangleStateCreateInfoEXT.html)

```julia
struct PipelineDiscardRectangleStateCreateInfoEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `flags::UInt32`
  * `discard_rectangle_mode::Vulkan.DiscardRectangleModeEXT`
  * `discard_rectangles::Vector{Vulkan.Rect2D}`
