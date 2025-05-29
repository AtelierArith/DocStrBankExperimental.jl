拡張: VK*EXT*descriptor_buffer

引数:

  * `command_buffer::CommandBuffer` (externsync)
  * `pipeline_bind_point::PipelineBindPoint`
  * `layout::PipelineLayout`
  * `buffer_indices::Vector{UInt32}`
  * `offsets::Vector{UInt64}`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCmdSetDescriptorBufferOffsetsEXT.html)

```julia
_cmd_set_descriptor_buffer_offsets_ext(
    command_buffer,
    pipeline_bind_point::Vulkan.PipelineBindPoint,
    layout,
    buffer_indices::AbstractArray,
    offsets::AbstractArray
)

```
