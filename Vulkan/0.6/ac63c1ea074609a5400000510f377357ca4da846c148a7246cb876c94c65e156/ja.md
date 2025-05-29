拡張: VK*NV*device*generated*commands

引数:

  * `pipeline_bind_point::PipelineBindPoint`
  * `pipeline::Pipeline`
  * `indirect_commands_layout::IndirectCommandsLayoutNV`
  * `streams::Vector{IndirectCommandsStreamNV}`
  * `sequences_count::UInt32`
  * `preprocess_buffer::Buffer`
  * `preprocess_offset::UInt64`
  * `preprocess_size::UInt64`
  * `sequences_count_offset::UInt64`
  * `sequences_index_offset::UInt64`
  * `next::Any`: デフォルトは `C_NULL`
  * `sequences_count_buffer::Buffer`: デフォルトは `C_NULL`
  * `sequences_index_buffer::Buffer`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkGeneratedCommandsInfoNV.html)

```julia
GeneratedCommandsInfoNV(
    pipeline_bind_point::Vulkan.PipelineBindPoint,
    pipeline::Vulkan.Pipeline,
    indirect_commands_layout::Vulkan.IndirectCommandsLayoutNV,
    streams::AbstractArray,
    sequences_count::Integer,
    preprocess_buffer::Vulkan.Buffer,
    preprocess_offset::Integer,
    preprocess_size::Integer,
    sequences_count_offset::Integer,
    sequences_index_offset::Integer;
    next,
    sequences_count_buffer,
    sequences_index_buffer
) -> Vulkan.GeneratedCommandsInfoNV

```
