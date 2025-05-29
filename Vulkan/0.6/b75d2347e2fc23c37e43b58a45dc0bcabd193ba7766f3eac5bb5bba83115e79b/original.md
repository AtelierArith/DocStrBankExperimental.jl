Extension: VK_EXT_transform_feedback

Arguments:

  * `command_buffer::CommandBuffer` (externsync)
  * `counter_buffers::Vector{Buffer}`
  * `counter_buffer_offsets::Vector{UInt64}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCmdBeginTransformFeedbackEXT.html)

```julia
_cmd_begin_transform_feedback_ext(
    command_buffer,
    counter_buffers::AbstractArray;
    counter_buffer_offsets
)

```
