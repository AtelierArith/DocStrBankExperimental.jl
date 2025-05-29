引数:

  * `device::Device`
  * `command_pool::CommandPool` (externsync)
  * `command_buffers::Vector{CommandBuffer}` (externsync)

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkFreeCommandBuffers.html)

```julia
free_command_buffers(
    device,
    command_pool,
    command_buffers::AbstractArray
)

```
