引数:

  * `stage::ShaderStageFlag`
  * `_module::ShaderModule`
  * `name::String`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `flags::PipelineShaderStageCreateFlag`: デフォルトは `0`
  * `specialization_info::_SpecializationInfo`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineShaderStageCreateInfo.html)

```julia
_PipelineShaderStageCreateInfo(
    stage::Vulkan.ShaderStageFlag,
    _module,
    name::AbstractString;
    next,
    flags,
    specialization_info
) -> Vulkan._PipelineShaderStageCreateInfo

```
