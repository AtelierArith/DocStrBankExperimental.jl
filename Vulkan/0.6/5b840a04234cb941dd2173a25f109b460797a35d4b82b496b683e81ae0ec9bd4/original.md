Extension: VK_KHR_push_descriptor

Arguments:

  * `command_buffer::CommandBuffer` (externsync)
  * `pipeline_bind_point::PipelineBindPoint`
  * `layout::PipelineLayout`
  * `set::UInt32`
  * `descriptor_writes::Vector{WriteDescriptorSet}`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCmdPushDescriptorSetKHR.html)

```julia
cmd_push_descriptor_set_khr(
    command_buffer,
    pipeline_bind_point::Vulkan.PipelineBindPoint,
    layout,
    set::Integer,
    descriptor_writes::AbstractArray
)

```
