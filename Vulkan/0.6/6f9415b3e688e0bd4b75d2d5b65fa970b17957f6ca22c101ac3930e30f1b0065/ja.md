引数:

  * `stage::ShaderStageFlag`
  * `_module::ShaderModule`
  * `name::String`
  * `next::Any`: デフォルトは `C_NULL`
  * `flags::PipelineShaderStageCreateFlag`: デフォルトは `0`
  * `specialization_info::SpecializationInfo`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineShaderStageCreateInfo.html)

```julia
PipelineShaderStageCreateInfo(
    stage::Vulkan.ShaderStageFlag,
    _module::Vulkan.ShaderModule,
    name::AbstractString;
    next,
    flags,
    specialization_info
) -> Vulkan.PipelineShaderStageCreateInfo

```
