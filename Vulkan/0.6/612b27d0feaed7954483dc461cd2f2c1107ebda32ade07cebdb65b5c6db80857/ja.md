拡張: VK*EXT*transform_feedback

引数:

  * `command_buffer::CommandBuffer` (externsync)
  * `counter_buffers::Vector{Buffer}`
  * `counter_buffer_offsets::Vector{UInt64}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCmdBeginTransformFeedbackEXT.html)

```julia
cmd_begin_transform_feedback_ext(
    command_buffer,
    counter_buffers::AbstractArray;
    counter_buffer_offsets
)

```
