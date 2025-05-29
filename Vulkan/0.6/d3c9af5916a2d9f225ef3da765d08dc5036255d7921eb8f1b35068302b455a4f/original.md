Extension: VK_NV_device_generated_commands

Arguments:

  * `command_buffer::CommandBuffer` (externsync)
  * `pipeline_bind_point::PipelineBindPoint`
  * `pipeline::Pipeline`
  * `group_index::UInt32`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCmdBindPipelineShaderGroupNV.html)

```julia
cmd_bind_pipeline_shader_group_nv(
    command_buffer,
    pipeline_bind_point::Vulkan.PipelineBindPoint,
    pipeline,
    group_index::Integer
)

```
