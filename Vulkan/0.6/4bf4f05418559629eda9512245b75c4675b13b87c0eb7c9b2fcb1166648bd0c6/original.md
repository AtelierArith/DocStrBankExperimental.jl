Arguments:

  * `stage::ShaderStageFlag`
  * `_module::ShaderModule`
  * `name::String`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `flags::PipelineShaderStageCreateFlag`: defaults to `0`
  * `specialization_info::_SpecializationInfo`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineShaderStageCreateInfo.html)

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
