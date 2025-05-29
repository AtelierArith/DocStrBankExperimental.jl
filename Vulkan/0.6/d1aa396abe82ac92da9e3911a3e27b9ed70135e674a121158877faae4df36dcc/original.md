Extension: VK_EXT_shader_module_identifier

Arguments:

  * `identifier_size::UInt32`
  * `identifier::NTuple{Int(VK_MAX_SHADER_MODULE_IDENTIFIER_SIZE_EXT), UInt8}`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkShaderModuleIdentifierEXT.html)

```julia
_ShaderModuleIdentifierEXT(
    identifier_size::Integer,
    identifier::NTuple{32, UInt8};
    next
) -> Vulkan._ShaderModuleIdentifierEXT

```
