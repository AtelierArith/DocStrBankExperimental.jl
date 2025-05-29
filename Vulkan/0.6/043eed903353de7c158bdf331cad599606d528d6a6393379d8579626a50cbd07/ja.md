VkIndirectCommandsLayoutTokenNVの高レベルラッパー。

拡張: VK*NV*device*generated*commands

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkIndirectCommandsLayoutTokenNV.html)

```julia
struct IndirectCommandsLayoutTokenNV <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `token_type::Vulkan.IndirectCommandsTokenTypeNV`
  * `stream::UInt32`
  * `offset::UInt32`
  * `vertex_binding_unit::UInt32`
  * `vertex_dynamic_stride::Bool`
  * `pushconstant_pipeline_layout::Union{Ptr{Nothing}, Vulkan.PipelineLayout}`
  * `pushconstant_shader_stage_flags::Vulkan.ShaderStageFlag`
  * `pushconstant_offset::UInt32`
  * `pushconstant_size::UInt32`
  * `indirect_state_flags::Vulkan.IndirectStateFlagNV`
  * `index_types::Vector{Vulkan.IndexType}`
  * `index_type_values::Vector{UInt32}`
