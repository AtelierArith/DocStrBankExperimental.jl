High-level wrapper for VkPhysicalDeviceShaderCoreProperties2AMD.

Extension: VK_AMD_shader_core_properties2

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceShaderCoreProperties2AMD.html)

```julia
struct PhysicalDeviceShaderCoreProperties2AMD <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `shader_core_features::Vulkan.ShaderCorePropertiesFlagAMD`
  * `active_compute_unit_count::UInt32`
