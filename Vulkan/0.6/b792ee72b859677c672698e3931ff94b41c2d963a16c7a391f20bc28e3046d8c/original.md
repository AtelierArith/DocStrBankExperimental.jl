Extension: VK_EXT_shader_module_identifier

Arguments:

  * `shader_module_identifier_algorithm_uuid::NTuple{Int(VK_UUID_SIZE), UInt8}`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceShaderModuleIdentifierPropertiesEXT.html)

```julia
PhysicalDeviceShaderModuleIdentifierPropertiesEXT(
    shader_module_identifier_algorithm_uuid::NTuple{16, UInt8};
    next
) -> Vulkan.PhysicalDeviceShaderModuleIdentifierPropertiesEXT

```
