引数:

  * `command_buffer::CommandBuffer` (externsync)
  * `pipeline_bind_point::PipelineBindPoint`
  * `layout::PipelineLayout`
  * `first_set::UInt32`
  * `descriptor_sets::Vector{DescriptorSet}`
  * `dynamic_offsets::Vector{UInt32}`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCmdBindDescriptorSets.html)

```julia
cmd_bind_descriptor_sets(
    command_buffer,
    pipeline_bind_point::Vulkan.PipelineBindPoint,
    layout,
    first_set::Integer,
    descriptor_sets::AbstractArray,
    dynamic_offsets::AbstractArray
)

```
