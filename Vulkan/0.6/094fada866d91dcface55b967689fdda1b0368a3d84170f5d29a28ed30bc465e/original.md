Arguments:

  * `command_buffer::CommandBuffer`
  * `device_mask::UInt32`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCommandBufferSubmitInfo.html)

```julia
CommandBufferSubmitInfo(
    command_buffer::Vulkan.CommandBuffer,
    device_mask::Integer;
    next
) -> Vulkan.CommandBufferSubmitInfo

```
