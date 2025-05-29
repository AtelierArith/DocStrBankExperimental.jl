VkPipelineViewportSwizzleStateCreateInfoNVの高レベルラッパー。

拡張: VK*NV*viewport_swizzle

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineViewportSwizzleStateCreateInfoNV.html)

```julia
struct PipelineViewportSwizzleStateCreateInfoNV <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `flags::UInt32`
  * `viewport_swizzles::Vector{Vulkan.ViewportSwizzleNV}`
