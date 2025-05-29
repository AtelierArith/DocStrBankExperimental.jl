Extension: VK_EXT_shader_module_identifier

Arguments:

  * `identifier::Vector{UInt8}`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `identifier_size::UInt32`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineShaderStageModuleIdentifierCreateInfoEXT.html)

```julia
_PipelineShaderStageModuleIdentifierCreateInfoEXT(
    identifier::AbstractArray;
    next,
    identifier_size
) -> Vulkan._PipelineShaderStageModuleIdentifierCreateInfoEXT

```
