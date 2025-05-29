Arguments:

  * `command_pool::CommandPool`
  * `level::CommandBufferLevel`
  * `command_buffer_count::UInt32`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCommandBufferAllocateInfo.html)

```julia
_CommandBufferAllocateInfo(
    command_pool,
    level::Vulkan.CommandBufferLevel,
    command_buffer_count::Integer;
    next
) -> Vulkan._CommandBufferAllocateInfo

```
