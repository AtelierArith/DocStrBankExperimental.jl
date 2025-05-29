拡張: VK*NV*device*generated*commands

引数:

  * `pipeline_bind_point::PipelineBindPoint`
  * `pipeline::Pipeline`
  * `indirect_commands_layout::IndirectCommandsLayoutNV`
  * `max_sequences_count::UInt32`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkGeneratedCommandsMemoryRequirementsInfoNV.html)

```julia
_GeneratedCommandsMemoryRequirementsInfoNV(
    pipeline_bind_point::Vulkan.PipelineBindPoint,
    pipeline,
    indirect_commands_layout,
    max_sequences_count::Integer;
    next
) -> Vulkan._GeneratedCommandsMemoryRequirementsInfoNV

```
