引数:

  * `command_buffer::CommandBuffer` (externsync)
  * `src_buffer::Buffer`
  * `dst_buffer::Buffer`
  * `regions::Vector{_BufferCopy}`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCmdCopyBuffer.html)

```julia
_cmd_copy_buffer(
    command_buffer,
    src_buffer,
    dst_buffer,
    regions::AbstractArray
)

```
