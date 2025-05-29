Arguments:

  * `command_buffer::CommandBuffer` (externsync)
  * `attachments::Vector{_ClearAttachment}`
  * `rects::Vector{_ClearRect}`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCmdClearAttachments.html)

```julia
_cmd_clear_attachments(
    command_buffer,
    attachments::AbstractArray,
    rects::AbstractArray
)

```
