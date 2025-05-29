Extension: VK_EXT_descriptor_buffer

Arguments:

  * `command_buffer::CommandBuffer` (externsync)
  * `pipeline_bind_point::PipelineBindPoint`
  * `layout::PipelineLayout`
  * `buffer_indices::Vector{UInt32}`
  * `offsets::Vector{UInt64}`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCmdSetDescriptorBufferOffsetsEXT.html)

```julia
cmd_set_descriptor_buffer_offsets_ext(
    command_buffer,
    pipeline_bind_point::Vulkan.PipelineBindPoint,
    layout,
    buffer_indices::AbstractArray,
    offsets::AbstractArray
)

```
