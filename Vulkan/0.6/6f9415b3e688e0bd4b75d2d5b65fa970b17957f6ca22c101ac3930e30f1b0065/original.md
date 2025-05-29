Arguments:

  * `stage::ShaderStageFlag`
  * `_module::ShaderModule`
  * `name::String`
  * `next::Any`: defaults to `C_NULL`
  * `flags::PipelineShaderStageCreateFlag`: defaults to `0`
  * `specialization_info::SpecializationInfo`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineShaderStageCreateInfo.html)

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
