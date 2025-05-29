Extension: VK_EXT_line_rasterization

Arguments:

  * `command_buffer::CommandBuffer` (externsync)
  * `line_stipple_factor::UInt32`
  * `line_stipple_pattern::UInt16`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCmdSetLineStippleEXT.html)

```julia
cmd_set_line_stipple_ext(
    command_buffer,
    line_stipple_factor::Integer,
    line_stipple_pattern::Integer
)

```
