Extension: VK_NV_memory_decompression

Arguments:

  * `command_buffer::CommandBuffer` (externsync)
  * `indirect_commands_address::UInt64`
  * `indirect_commands_count_address::UInt64`
  * `stride::UInt32`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCmdDecompressMemoryIndirectCountNV.html)

```julia
_cmd_decompress_memory_indirect_count_nv(
    command_buffer,
    indirect_commands_address::Integer,
    indirect_commands_count_address::Integer,
    stride::Integer
)

```
