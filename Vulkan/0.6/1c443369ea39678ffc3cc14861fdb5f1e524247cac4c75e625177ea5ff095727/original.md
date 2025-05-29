Extension: VK_KHR_synchronization2

Arguments:

  * `command_buffer::CommandBuffer` (externsync)
  * `dst_buffer::Buffer`
  * `dst_offset::UInt64`
  * `marker::UInt32`
  * `stage::UInt64`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCmdWriteBufferMarker2AMD.html)

```julia
_cmd_write_buffer_marker_2_amd(
    command_buffer,
    dst_buffer,
    dst_offset::Integer,
    marker::Integer;
    stage
)

```
