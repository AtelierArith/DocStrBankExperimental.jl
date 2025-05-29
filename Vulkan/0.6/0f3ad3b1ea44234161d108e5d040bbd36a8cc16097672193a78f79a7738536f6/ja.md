引数:

  * `command_buffer::CommandBuffer` (externsync)
  * `layout::PipelineLayout`
  * `stage_flags::ShaderStageFlag`
  * `offset::UInt32`
  * `size::UInt32`
  * `values::Ptr{Cvoid}` (サイズバイトの有効なポインタでなければなりません)

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCmdPushConstants.html)

```julia
cmd_push_constants(
    command_buffer,
    layout,
    stage_flags::Vulkan.ShaderStageFlag,
    offset::Integer,
    size::Integer,
    values::Ptr{Nothing}
)

```
