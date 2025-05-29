VkGeneratedCommandsInfoNVの高レベルラッパー。

拡張: VK*NV*device*generated*commands

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkGeneratedCommandsInfoNV.html)

```julia
struct GeneratedCommandsInfoNV <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `pipeline_bind_point::Vulkan.PipelineBindPoint`
  * `pipeline::Vulkan.Pipeline`
  * `indirect_commands_layout::Vulkan.IndirectCommandsLayoutNV`
  * `streams::Vector{Vulkan.IndirectCommandsStreamNV}`
  * `sequences_count::UInt32`
  * `preprocess_buffer::Vulkan.Buffer`
  * `preprocess_offset::UInt64`
  * `preprocess_size::UInt64`
  * `sequences_count_buffer::Union{Ptr{Nothing}, Vulkan.Buffer}`
  * `sequences_count_offset::UInt64`
  * `sequences_index_buffer::Union{Ptr{Nothing}, Vulkan.Buffer}`
  * `sequences_index_offset::UInt64`
