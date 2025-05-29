拡張: VK*NV*device*generated*commands

引数:

  * `pipeline_bind_point::PipelineBindPoint`
  * `pipeline::Pipeline`
  * `indirect_commands_layout::IndirectCommandsLayoutNV`
  * `max_sequences_count::UInt32`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkGeneratedCommandsMemoryRequirementsInfoNV.html)

```julia
GeneratedCommandsMemoryRequirementsInfoNV(
    pipeline_bind_point::Vulkan.PipelineBindPoint,
    pipeline::Vulkan.Pipeline,
    indirect_commands_layout::Vulkan.IndirectCommandsLayoutNV,
    max_sequences_count::Integer;
    next
) -> Vulkan.GeneratedCommandsMemoryRequirementsInfoNV

```
