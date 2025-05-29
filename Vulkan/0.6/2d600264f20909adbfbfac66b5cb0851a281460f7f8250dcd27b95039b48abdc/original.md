High-level wrapper for VkShaderModuleIdentifierEXT.

Extension: VK_EXT_shader_module_identifier

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkShaderModuleIdentifierEXT.html)

```julia
struct ShaderModuleIdentifierEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `identifier_size::UInt32`
  * `identifier::NTuple{32, UInt8}`
