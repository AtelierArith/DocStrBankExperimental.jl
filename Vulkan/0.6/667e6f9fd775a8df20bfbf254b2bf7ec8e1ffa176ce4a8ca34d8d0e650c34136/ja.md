拡張: VK*NV*device*generated*commands

引数:

  * `token_type::IndirectCommandsTokenTypeNV`
  * `stream::UInt32`
  * `offset::UInt32`
  * `vertex_binding_unit::UInt32`
  * `vertex_dynamic_stride::Bool`
  * `pushconstant_offset::UInt32`
  * `pushconstant_size::UInt32`
  * `index_types::Vector{IndexType}`
  * `index_type_values::Vector{UInt32}`
  * `next::Any`: デフォルトは `C_NULL`
  * `pushconstant_pipeline_layout::PipelineLayout`: デフォルトは `C_NULL`
  * `pushconstant_shader_stage_flags::ShaderStageFlag`: デフォルトは `0`
  * `indirect_state_flags::IndirectStateFlagNV`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkIndirectCommandsLayoutTokenNV.html)

```julia
IndirectCommandsLayoutTokenNV(
    token_type::Vulkan.IndirectCommandsTokenTypeNV,
    stream::Integer,
    offset::Integer,
    vertex_binding_unit::Integer,
    vertex_dynamic_stride::Bool,
    pushconstant_offset::Integer,
    pushconstant_size::Integer,
    index_types::AbstractArray,
    index_type_values::AbstractArray;
    next,
    pushconstant_pipeline_layout,
    pushconstant_shader_stage_flags,
    indirect_state_flags
) -> Vulkan.IndirectCommandsLayoutTokenNV

```
