拡張: VK*KHR*push_descriptor

引数:

  * `command_buffer::CommandBuffer` (externsync)
  * `descriptor_update_template::DescriptorUpdateTemplate`
  * `layout::PipelineLayout`
  * `set::UInt32`
  * `data::Ptr{Cvoid}`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCmdPushDescriptorSetWithTemplateKHR.html)

```julia
_cmd_push_descriptor_set_with_template_khr(
    command_buffer,
    descriptor_update_template,
    layout,
    set::Integer,
    data::Ptr{Nothing}
)

```
