拡張: VK*EXT*shader*module*identifier

引数:

  * `shader_module_identifier_algorithm_uuid::NTuple{Int(VK_UUID_SIZE), UInt8}`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceShaderModuleIdentifierPropertiesEXT.html)

```julia
PhysicalDeviceShaderModuleIdentifierPropertiesEXT(
    shader_module_identifier_algorithm_uuid::NTuple{16, UInt8};
    next
) -> Vulkan.PhysicalDeviceShaderModuleIdentifierPropertiesEXT

```
