VkGeneratedCommandsMemoryRequirementsInfoNVの高レベルラッパー。

拡張: VK*NV*device*generated*commands

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkGeneratedCommandsMemoryRequirementsInfoNV.html)

```julia
struct GeneratedCommandsMemoryRequirementsInfoNV <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `pipeline_bind_point::Vulkan.PipelineBindPoint`
  * `pipeline::Vulkan.Pipeline`
  * `indirect_commands_layout::Vulkan.IndirectCommandsLayoutNV`
  * `max_sequences_count::UInt32`
