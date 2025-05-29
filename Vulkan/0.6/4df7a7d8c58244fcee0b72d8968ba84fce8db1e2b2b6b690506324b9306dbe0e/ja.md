VkPipelineViewportExclusiveScissorStateCreateInfoNVの高レベルラッパー。

拡張: VK*NV*scissor_exclusive

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineViewportExclusiveScissorStateCreateInfoNV.html)

```julia
struct PipelineViewportExclusiveScissorStateCreateInfoNV <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `exclusive_scissors::Vector{Vulkan.Rect2D}`
