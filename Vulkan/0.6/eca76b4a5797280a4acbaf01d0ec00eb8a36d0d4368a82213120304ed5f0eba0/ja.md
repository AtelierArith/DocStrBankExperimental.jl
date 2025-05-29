拡張: VK*NV*copy*memory*indirect

引数:

  * `command_buffer::CommandBuffer` (externsync)
  * `copy_buffer_address::UInt64`
  * `copy_count::UInt32`
  * `stride::UInt32`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCmdCopyMemoryIndirectNV.html)

```julia
_cmd_copy_memory_indirect_nv(
    command_buffer,
    copy_buffer_address::Integer,
    copy_count::Integer,
    stride::Integer
)

```
