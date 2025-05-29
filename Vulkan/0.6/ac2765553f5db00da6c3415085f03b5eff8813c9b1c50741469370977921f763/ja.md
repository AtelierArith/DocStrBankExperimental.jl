VkCommandBufferBeginInfoの高レベルラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCommandBufferBeginInfo.html)

```julia
struct CommandBufferBeginInfo <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `flags::Vulkan.CommandBufferUsageFlag`
  * `inheritance_info::Union{Ptr{Nothing}, Vulkan.CommandBufferInheritanceInfo}`
