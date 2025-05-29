VkPipelineViewportStateCreateInfoの高レベルラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineViewportStateCreateInfo.html)

```julia
struct PipelineViewportStateCreateInfo <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `flags::UInt32`
  * `viewports::Union{Ptr{Nothing}, Vector{Vulkan.Viewport}}`
  * `scissors::Union{Ptr{Nothing}, Vector{Vulkan.Rect2D}}`
