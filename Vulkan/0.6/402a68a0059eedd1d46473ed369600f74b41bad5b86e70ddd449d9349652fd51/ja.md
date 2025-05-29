引数:

  * `command_buffer::CommandBuffer` (externsync)
  * `buffers::Vector{Buffer}`
  * `offsets::Vector{UInt64}`
  * `sizes::Vector{UInt64}`: デフォルトは `C_NULL`
  * `strides::Vector{UInt64}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCmdBindVertexBuffers2.html)

```julia
_cmd_bind_vertex_buffers_2(
    command_buffer,
    buffers::AbstractArray,
    offsets::AbstractArray;
    sizes,
    strides
)

```
