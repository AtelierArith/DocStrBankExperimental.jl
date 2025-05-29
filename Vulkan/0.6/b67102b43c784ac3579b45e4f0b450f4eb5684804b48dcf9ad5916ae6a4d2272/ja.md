引数:

  * `command_buffer::CommandBuffer` (externsync)
  * `dst_buffer::Buffer`
  * `dst_offset::UInt64`
  * `data_size::UInt64`
  * `data::Ptr{Cvoid}` (必ず `data_size` バイトの有効なポインタである必要があります)

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCmdUpdateBuffer.html)

```julia
cmd_update_buffer(
    command_buffer,
    dst_buffer,
    dst_offset::Integer,
    data_size::Integer,
    data::Ptr{Nothing}
)

```
