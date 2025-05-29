拡張: VK*EXT*shader*module*identifier

引数:

  * `identifier_size::UInt32`
  * `identifier::NTuple{Int(VK_MAX_SHADER_MODULE_IDENTIFIER_SIZE_EXT), UInt8}`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkShaderModuleIdentifierEXT.html)

```julia
ShaderModuleIdentifierEXT(
    identifier_size::Integer,
    identifier::NTuple{32, UInt8};
    next
) -> Vulkan.ShaderModuleIdentifierEXT

```
