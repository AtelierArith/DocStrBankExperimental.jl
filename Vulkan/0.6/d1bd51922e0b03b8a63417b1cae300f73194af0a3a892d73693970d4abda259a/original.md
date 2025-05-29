Arguments:

  * `command_buffer::CommandBuffer`
  * `device_mask::UInt32`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCommandBufferSubmitInfo.html)

```julia
_CommandBufferSubmitInfo(
    command_buffer,
    device_mask::Integer;
    next
) -> Vulkan._CommandBufferSubmitInfo

```
