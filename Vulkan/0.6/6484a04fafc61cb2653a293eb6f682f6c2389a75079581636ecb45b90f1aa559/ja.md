引数:

  * `command_buffer::CommandBuffer` (externsync)
  * `buffers::Vector{Buffer}`
  * `offsets::Vector{UInt64}`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCmdBindVertexBuffers.html)

```julia
cmd_bind_vertex_buffers(
    command_buffer,
    buffers::AbstractArray,
    offsets::AbstractArray
)

```
