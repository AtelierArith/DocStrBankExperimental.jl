Extension: VK_KHR_push_descriptor

Arguments:

  * `command_buffer::CommandBuffer` (externsync)
  * `descriptor_update_template::DescriptorUpdateTemplate`
  * `layout::PipelineLayout`
  * `set::UInt32`
  * `data::Ptr{Cvoid}`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCmdPushDescriptorSetWithTemplateKHR.html)

```julia
cmd_push_descriptor_set_with_template_khr(
    command_buffer,
    descriptor_update_template,
    layout,
    set::Integer,
    data::Ptr{Nothing}
)

```
