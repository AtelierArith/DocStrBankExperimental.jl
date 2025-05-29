拡張: VK*EXT*shader*module*identifier

引数:

  * `shader_module_identifier::Bool`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceShaderModuleIdentifierFeaturesEXT.html)

```julia
_PhysicalDeviceShaderModuleIdentifierFeaturesEXT(
    shader_module_identifier::Bool;
    next
) -> Vulkan._PhysicalDeviceShaderModuleIdentifierFeaturesEXT

```
