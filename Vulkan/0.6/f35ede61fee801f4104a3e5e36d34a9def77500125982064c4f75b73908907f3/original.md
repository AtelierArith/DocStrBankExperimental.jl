High-level wrapper for VkCommandBufferAllocateInfo.

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCommandBufferAllocateInfo.html)

```julia
struct CommandBufferAllocateInfo <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `command_pool::Vulkan.CommandPool`
  * `level::Vulkan.CommandBufferLevel`
  * `command_buffer_count::UInt32`
