High-level wrapper for VkRenderPassMultiviewCreateInfo.

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkRenderPassMultiviewCreateInfo.html)

```julia
struct RenderPassMultiviewCreateInfo <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `view_masks::Vector{UInt32}`
  * `view_offsets::Vector{Int32}`
  * `correlation_masks::Vector{UInt32}`
