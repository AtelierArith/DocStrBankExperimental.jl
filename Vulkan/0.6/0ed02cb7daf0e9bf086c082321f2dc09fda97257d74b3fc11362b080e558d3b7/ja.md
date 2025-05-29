VkCommandBufferSubmitInfoの高レベルラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCommandBufferSubmitInfo.html)

```julia
struct CommandBufferSubmitInfo <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `command_buffer::Vulkan.CommandBuffer`
  * `device_mask::UInt32`
