Arguments:

  * `device::Device`
  * `command_pool::CommandPool` (externsync)
  * `command_buffers::Vector{CommandBuffer}` (externsync)

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkFreeCommandBuffers.html)

```julia
_free_command_buffers(
    device,
    command_pool,
    command_buffers::AbstractArray
)

```
