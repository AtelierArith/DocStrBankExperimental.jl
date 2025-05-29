Extension: VK_EXT_color_write_enable

Arguments:

  * `command_buffer::CommandBuffer` (externsync)
  * `color_write_enables::Vector{Bool}`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCmdSetColorWriteEnableEXT.html)

```julia
cmd_set_color_write_enable_ext(
    command_buffer,
    color_write_enables::AbstractArray
)

```
