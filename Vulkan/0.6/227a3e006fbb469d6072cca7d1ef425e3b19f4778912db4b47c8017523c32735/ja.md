引数:

  * `command_pool::CommandPool`
  * `level::CommandBufferLevel`
  * `command_buffer_count::UInt32`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCommandBufferAllocateInfo.html)

```julia
CommandBufferAllocateInfo(
    command_pool::Vulkan.CommandPool,
    level::Vulkan.CommandBufferLevel,
    command_buffer_count::Integer;
    next
) -> Vulkan.CommandBufferAllocateInfo

```
